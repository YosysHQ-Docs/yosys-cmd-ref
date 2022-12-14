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
                read_verilog -lib -specify +/quicklogic/cells_sim.v +/quicklogic/pp3_cells_sim.v
                read_verilog -lib -specify +/quicklogic/lut_sim.v
                hierarchy -check -top <top>

            coarse:
                proc
                flatten
                tribuf -logic
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
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean
                alumacc
                pmuxtree
                opt
                memory -nomap
                opt_clean

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map -iattr -attr !ram_block -attr !rom_block -attr logic_block -attr syn_ramstyle=auto -attr syn_ramstyle=registers -attr syn_romstyle=auto -attr syn_romstyle=logic
                opt -undriven -fine

            map_gates:
                techmap
                opt -fast
                muxcover -mux8 -mux4

            map_ffs:
                opt_expr
                dfflegalize -cell $_DFFSRE_PPPP_ 0 -cell $_DLATCH_?_ x
                techmap -map +/quicklogic/pp3_cells_map.v -map +/quicklogic/pp3_ffs_map.v
                opt_expr -mux_undef

            map_luts:
                techmap -map +/quicklogic/pp3_latches_map.v
                read_verilog -lib -specify -icells +/quicklogic/abc9_model.v
                techmap -map +/quicklogic/abc9_map.v
                abc9 -maxlut 4 -dff
                techmap -map +/quicklogic/abc9_unmap.v
                clean

            map_cells:
                techmap -map +/quicklogic/pp3_lut_map.v
                clean

            check:
                autoname
                hierarchy -check
                stat
                check -noinit

            iomap:
                clkbufmap -inpad ckpad Q:P
                iopadmap -bits -outpad outpad A:P -inpad inpad Q:P -tinoutpad bipad EN:Q:A:P A:top

            finalize:
                setundef -zero -params -undriven
                hilomap -hicell logic_1 A -locell logic_0 A -singleton A:top
                opt_clean -purge
                check
                blackbox =A:whitebox

            blif:
                write_blif -attr -param -auto-top 

            verilog:
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
                read_verilog -lib -specify +/quicklogic/cells_sim.v +/quicklogic/pp3_cells_sim.v
                read_verilog -lib -specify +/quicklogic/lut_sim.v
                hierarchy -check -top <top>
        
            coarse:
                proc
                flatten
                tribuf -logic
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
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean
                alumacc
                pmuxtree
                opt
                memory -nomap
                opt_clean
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map -iattr -attr !ram_block -attr !rom_block -attr logic_block -attr syn_ramstyle=auto -attr syn_ramstyle=registers -attr syn_romstyle=auto -attr syn_romstyle=logic
                opt -undriven -fine
        
            map_gates:
                techmap
                opt -fast
                muxcover -mux8 -mux4
        
            map_ffs:
                opt_expr
                dfflegalize -cell $_DFFSRE_PPPP_ 0 -cell $_DLATCH_?_ x
                techmap -map +/quicklogic/pp3_cells_map.v -map +/quicklogic/pp3_ffs_map.v
                opt_expr -mux_undef
        
            map_luts:
                techmap -map +/quicklogic/pp3_latches_map.v
                read_verilog -lib -specify -icells +/quicklogic/abc9_model.v
                techmap -map +/quicklogic/abc9_map.v
                abc9 -maxlut 4 -dff
                techmap -map +/quicklogic/abc9_unmap.v
                clean
        
            map_cells:
                techmap -map +/quicklogic/pp3_lut_map.v
                clean
        
            check:
                autoname
                hierarchy -check
                stat
                check -noinit
        
            iomap:
                clkbufmap -inpad ckpad Q:P
                iopadmap -bits -outpad outpad A:P -inpad inpad Q:P -tinoutpad bipad EN:Q:A:P A:top
        
            finalize:
                setundef -zero -params -undriven
                hilomap -hicell logic_1 A -locell logic_0 A -singleton A:top
                opt_clean -purge
                check
                blackbox =A:whitebox
        
            blif:
                write_blif -attr -param -auto-top 
        
            verilog:
                write_verilog -noattr -nohex <file-name>
        
