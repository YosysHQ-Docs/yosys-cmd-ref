=================================================
synth_quicklogic - Synthesis for QuickLogic FPGAs
=================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth_quicklogic`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth_quicklogic [options]

    ::

        This command runs synthesis for QuickLogic FPGAs


    .. code:: yoscrypt

        -top <module>

    ::

             use the specified module as top module


    .. code:: yoscrypt

        -family <family>

    ::

            run synthesis for the specified QuickLogic architecture
            generate the synthesis netlist for the specified family.
            supported values:
            - pp3: PolarPro 3 
            - qlf_k6n10f: K6N10f


    .. code:: yoscrypt

        -nodsp

    ::

            do not use dsp_t1_* to implement multipliers and associated logic
            (qlf_k6n10f only).


    .. code:: yoscrypt

        -nocarry

    ::

            do not use adder_carry cells in output netlist.


    .. code:: yoscrypt

        -nobram

    ::

            do not use block RAM cells in output netlist.


    .. code:: yoscrypt

        -bramtypes

    ::

            Emit specialized BRAM cells for particular address and data width
            configurations.


    .. code:: yoscrypt

        -blif <file>

    ::

            write the design to the specified BLIF file. writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -verilog <file>

    ::

            write the design to the specified verilog file. writing of an output
            file is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -abc

    ::

            use old ABC flow, which has generally worse mapping results but is less
            likely to have bugs.


    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib -specify +/quicklogic/common/cells_sim.v +/quicklogic/<family>/cells_sim.v
                hierarchy -check -top <top>

            prepare:
                proc
                flatten
                tribuf -logic                       (for pp3)
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm
                opt
                wreduce
                peepopt
                opt_clean
                share

            map_dsp:    (for qlf_k6n10f, skip if -nodsp)
                wreduce t:$mul
                ql_dsp_macc
                techmap -map +/mul2dsp.v -D DSP_A_MAXWIDTH=20 -D DSP_B_MAXWIDTH=18 -D DSP_A_MINWIDTH=11 -D DSP_B_MINWIDTH=10 -D DSP_NAME=$__QL_MUL20X18
                techmap -map +/mul2dsp.v -D DSP_A_MAXWIDTH=10 -D DSP_B_MAXWIDTH=9 -D DSP_A_MINWIDTH=4 -D DSP_B_MINWIDTH=4 -D DSP_NAME=$__QL_MUL10X9
                chtype -set $mul t:$__soft_mul
                techmap -map +/quicklogic/<family>/dsp_map.v -D USE_DSP_CFG_PARAMS=0
                ql_dsp_simd
                techmap -map +/quicklogic/<family>/dsp_final_map.v
                ql_dsp_io_regs

            coarse:
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean
                alumacc
                pmuxtree
                opt
                memory -nomap
                opt_clean

            map_bram:    (for qlf_k6n10f, skip if -no_bram)
                memory_libmap -lib +/quicklogic/<family>/libmap_brams.txt
                ql_bram_merge
                techmap -map +/quicklogic/<family>/libmap_brams_map.v
                techmap -autoproc -map +/quicklogic/<family>/brams_map.v
                ql_bram_types    (if -bramtypes)

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map -iattr -attr !ram_block -attr !rom_block -attr logic_block -attr syn_ramstyle=auto -attr syn_ramstyle=registers -attr syn_romstyle=auto -attr syn_romstyle=logic
                opt -undriven -fine

            map_gates:
                techmap
                opt -fast
                muxcover -mux8 -mux4    (for pp3)

            map_ffs:
                opt_expr
                shregmap -minlen <min> -maxlen <max>    (for qlf_k6n10f)
                dfflegalize -cell <supported FF types>
                techmap -map +/quicklogic/<family>/cells_map.v    (for pp3)
                techmap -map +/quicklogic/<family>/ffs_map.v    (for ql_k6n10f)
                opt

            map_luts:    (for pp3)
                techmap -map +/quicklogic/<family>/latches_map.v
                read_verilog -lib -specify -icells +/quicklogic/<family>/abc9_model.v
                techmap -map +/quicklogic/<family>/abc9_map.v
                abc9 -maxlut 4 -dff
                techmap -map +/quicklogic/<family>/abc9_unmap.v
                clean

            map_luts:    (for qlf_k6n10f)
                abc9 -maxlut 6
                clean
                opt_lut

            map_cells:    (for pp3)
                techmap -map +/quicklogic/<family>/lut_map.v
                clean
                opt_lut

            check:
                autoname
                hierarchy -check
                stat
                check -noinit

            iomap:    (for pp3)
                clkbufmap -inpad ckpad Q:P
                iopadmap -bits -outpad outpad A:P -inpad inpad Q:P -tinoutpad bipad EN:Q:A:P A:top

            finalize:
                setundef -zero -params -undriven    (for pp3)
                opt_clean -purge
                check
                blackbox =A:whitebox

            blif:    (if -blif)
                write_blif -attr -param -auto-top 

            verilog:    (if -verilog)
                write_verilog -noattr -nohex <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
           synth_quicklogic [options]
        This command runs synthesis for QuickLogic FPGAs
        
            -top <module>
                 use the specified module as top module
        
            -family <family>
                run synthesis for the specified QuickLogic architecture
                generate the synthesis netlist for the specified family.
                supported values:
                - pp3: PolarPro 3 
                - qlf_k6n10f: K6N10f
        
            -nodsp
                do not use dsp_t1_* to implement multipliers and associated logic
                (qlf_k6n10f only).
        
            -nocarry
                do not use adder_carry cells in output netlist.
        
            -nobram
                do not use block RAM cells in output netlist.
        
            -bramtypes
                Emit specialized BRAM cells for particular address and data width
                configurations.
        
            -blif <file>
                write the design to the specified BLIF file. writing of an output file
                is omitted if this parameter is not specified.
        
            -verilog <file>
                write the design to the specified verilog file. writing of an output
                file is omitted if this parameter is not specified.
        
            -abc
                use old ABC flow, which has generally worse mapping results but is less
                likely to have bugs.
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -specify +/quicklogic/common/cells_sim.v +/quicklogic/<family>/cells_sim.v
                hierarchy -check -top <top>
        
            prepare:
                proc
                flatten
                tribuf -logic                       (for pp3)
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm
                opt
                wreduce
                peepopt
                opt_clean
                share
        
            map_dsp:    (for qlf_k6n10f, skip if -nodsp)
                wreduce t:$mul
                ql_dsp_macc
                techmap -map +/mul2dsp.v -D DSP_A_MAXWIDTH=20 -D DSP_B_MAXWIDTH=18 -D DSP_A_MINWIDTH=11 -D DSP_B_MINWIDTH=10 -D DSP_NAME=$__QL_MUL20X18
                techmap -map +/mul2dsp.v -D DSP_A_MAXWIDTH=10 -D DSP_B_MAXWIDTH=9 -D DSP_A_MINWIDTH=4 -D DSP_B_MINWIDTH=4 -D DSP_NAME=$__QL_MUL10X9
                chtype -set $mul t:$__soft_mul
                techmap -map +/quicklogic/<family>/dsp_map.v -D USE_DSP_CFG_PARAMS=0
                ql_dsp_simd
                techmap -map +/quicklogic/<family>/dsp_final_map.v
                ql_dsp_io_regs
        
            coarse:
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean
                alumacc
                pmuxtree
                opt
                memory -nomap
                opt_clean
        
            map_bram:    (for qlf_k6n10f, skip if -no_bram)
                memory_libmap -lib +/quicklogic/<family>/libmap_brams.txt
                ql_bram_merge
                techmap -map +/quicklogic/<family>/libmap_brams_map.v
                techmap -autoproc -map +/quicklogic/<family>/brams_map.v
                ql_bram_types    (if -bramtypes)
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map -iattr -attr !ram_block -attr !rom_block -attr logic_block -attr syn_ramstyle=auto -attr syn_ramstyle=registers -attr syn_romstyle=auto -attr syn_romstyle=logic
                opt -undriven -fine
        
            map_gates:
                techmap
                opt -fast
                muxcover -mux8 -mux4    (for pp3)
        
            map_ffs:
                opt_expr
                shregmap -minlen <min> -maxlen <max>    (for qlf_k6n10f)
                dfflegalize -cell <supported FF types>
                techmap -map +/quicklogic/<family>/cells_map.v    (for pp3)
                techmap -map +/quicklogic/<family>/ffs_map.v    (for ql_k6n10f)
                opt
        
            map_luts:    (for pp3)
                techmap -map +/quicklogic/<family>/latches_map.v
                read_verilog -lib -specify -icells +/quicklogic/<family>/abc9_model.v
                techmap -map +/quicklogic/<family>/abc9_map.v
                abc9 -maxlut 4 -dff
                techmap -map +/quicklogic/<family>/abc9_unmap.v
                clean
        
            map_luts:    (for qlf_k6n10f)
                abc9 -maxlut 6
                clean
                opt_lut
        
            map_cells:    (for pp3)
                techmap -map +/quicklogic/<family>/lut_map.v
                clean
                opt_lut
        
            check:
                autoname
                hierarchy -check
                stat
                check -noinit
        
            iomap:    (for pp3)
                clkbufmap -inpad ckpad Q:P
                iopadmap -bits -outpad outpad A:P -inpad inpad Q:P -tinoutpad bipad EN:Q:A:P A:top
        
            finalize:
                setundef -zero -params -undriven    (for pp3)
                opt_clean -purge
                check
                blackbox =A:whitebox
        
            blif:    (if -blif)
                write_blif -attr -param -auto-top 
        
            verilog:    (if -verilog)
                write_verilog -noattr -nohex <file-name>
        
