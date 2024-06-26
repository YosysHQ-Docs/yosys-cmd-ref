=========================================
synth_xilinx - synthesis for Xilinx FPGAs
=========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_xilinx
    :title: synthesis for Xilinx FPGAs



    .. code:: yoscrypt

        synth_xilinx [options]

    ::

        This command runs synthesis for Xilinx FPGAs. This command does not operate on
        partly selected designs. At the moment this command creates netlists that are
        compatible with 7-Series Xilinx devices.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module


    .. code:: yoscrypt

        -family <family>

    ::

            run synthesis for the specified Xilinx architecture
            generate the synthesis netlist for the specified family.
            supported values:
            - xcup: Ultrascale Plus
            - xcu: Ultrascale
            - xc7: Series 7 (default)
            - xc6s: Spartan 6
            - xc6v: Virtex 6
            - xc5v: Virtex 5 (EXPERIMENTAL)
            - xc4v: Virtex 4 (EXPERIMENTAL)
            - xc3sda: Spartan 3A DSP (EXPERIMENTAL)
            - xc3sa: Spartan 3A (EXPERIMENTAL)
            - xc3se: Spartan 3E (EXPERIMENTAL)
            - xc3s: Spartan 3 (EXPERIMENTAL)
            - xc2vp: Virtex 2 Pro (EXPERIMENTAL)
            - xc2v: Virtex 2 (EXPERIMENTAL)
            - xcve: Virtex E, Spartan 2E (EXPERIMENTAL)
            - xcv: Virtex, Spartan 2 (EXPERIMENTAL)


    .. code:: yoscrypt

        -edif <file>

    ::

            write the design to the specified edif file. writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -blif <file>

    ::

            write the design to the specified BLIF file. writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -ise

    ::

            generate an output netlist suitable for ISE


    .. code:: yoscrypt

        -nobram

    ::

            do not use block RAM cells in output netlist


    .. code:: yoscrypt

        -nolutram

    ::

            do not use distributed RAM cells in output netlist


    .. code:: yoscrypt

        -nosrl

    ::

            do not use distributed SRL cells in output netlist


    .. code:: yoscrypt

        -nocarry

    ::

            do not use XORCY/MUXCY/CARRY4 cells in output netlist


    .. code:: yoscrypt

        -nowidelut

    ::

            do not use MUXF[5-9] resources to implement LUTs larger than native for
            the target


    .. code:: yoscrypt

        -nodsp

    ::

            do not use DSP48*s to implement multipliers and associated logic


    .. code:: yoscrypt

        -noiopad

    ::

            disable I/O buffer insertion (useful for hierarchical or 
            out-of-context flows)


    .. code:: yoscrypt

        -noclkbuf

    ::

            disable automatic clock buffer insertion


    .. code:: yoscrypt

        -uram

    ::

            infer URAM288s for large memories (xcup only)


    .. code:: yoscrypt

        -widemux <int>

    ::

            enable inference of hard multiplexer resources (MUXF[78]) for muxes at
            or above this number of inputs (minimum value 2, recommended value >= 5)
            default: 0 (no inference)


    .. code:: yoscrypt

        -run <from_label>:<to_label>

    ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -flatten

    ::

            flatten design before synthesis


    .. code:: yoscrypt

        -dff

    ::

            run 'abc'/'abc9' with -dff option


    .. code:: yoscrypt

        -retime

    ::

            run 'abc' with '-D 1' option to enable flip-flop retiming.
            implies -dff.


    .. code:: yoscrypt

        -abc9

    ::

            use new ABC9 flow (EXPERIMENTAL)



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib -specify +/xilinx/cells_sim.v
                read_verilog -lib +/xilinx/cells_xtra.v
                hierarchy -check -auto-top

            prepare:
                proc
                flatten    (with '-flatten')
                tribuf -logic
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm
                opt
                wreduce [-keepdc]    (option for '-widemux')
                peepopt
                opt_clean
                muxpack        ('-widemux' only)
                pmux2shiftx    (skip if '-nosrl' and '-widemux=0')
                clean          (skip if '-nosrl' and '-widemux=0')

            map_dsp:    (skip if '-nodsp')
                memory_dff
                techmap -map +/mul2dsp.v -map +/xilinx/{family}_dsp_map.v {options}
                select a:mul2dsp
                setattr -unset mul2dsp
                opt_expr -fine
                wreduce
                select -clear
                xilinx_dsp -family <family>
                chtype -set $mul t:$__soft_mul

            coarse:
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v -D LUT_WIDTH=[46]
                alumacc
                share
                opt
                memory -nomap
                opt_clean

            map_memory:
                memory_libmap [...]
                techmap -map +/xilinx/lutrams_<family>_map.v
                techmap -map +/xilinx/brams_<family>_map.v

            map_ffram:
                opt -fast -full
                memory_map

            fine:
                simplemap t:$mux    ('-widemux' only)
                muxcover <internal options>    ('-widemux' only)
                opt -full
                xilinx_srl -variable -minlen 3    (skip if '-nosrl')
                techmap  -map +/techmap.v -D LUT_SIZE=[46] [-map +/xilinx/mux_map.v] -map +/xilinx/arith_map.v
                opt -fast

            map_cells:
                iopadmap -bits -outpad OBUF I:O -inpad IBUF O:I -toutpad OBUFT ~T:I:O -tinoutpad IOBUF ~T:O:I:IO A:top    (skip if '-noiopad')
                techmap -map +/techmap.v -map +/xilinx/cells_map.v
                clean

            map_ffs:
                dfflegalize -cell $_DFFE_?P?P_ 01 -cell $_SDFFE_?P?P_ 01 -cell $_DLATCH_?P?_ 01    (for xc6v, xc7, xcu, xcup)
                zinit -all w:* t:$_SDFFE_*    ('-dff' only)
                techmap -map +/xilinx/ff_map.v    ('-abc9' only)

            map_luts:
                opt_expr -mux_undef -noclkinv
                abc -luts 2:2,3,6:5[,10,20] [-dff] [-D 1]    (option for '-nowidelut', '-dff', '-retime')
                clean
                techmap -map +/xilinx/ff_map.v    (only if not '-abc9')
                xilinx_srl -fixed -minlen 3    (skip if '-nosrl')
                techmap -map +/xilinx/lut_map.v -map +/xilinx/cells_map.v -D LUT_WIDTH=[46]
                xilinx_dffopt [-lut4]
                opt_lut_ins -tech xilinx

            finalize:
                clkbufmap -buf BUFG O:I    (skip if '-noclkbuf')
                extractinv -inv INV O:I    (only if '-ise')
                clean

            check:
                hierarchy -check
                stat -tech xilinx
                check -noinit
                blackbox =A:whitebox

            edif:
                write_edif -pvector bra 

            blif:
                write_blif 

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_xilinx [options]
        
        This command runs synthesis for Xilinx FPGAs. This command does not operate on
        partly selected designs. At the moment this command creates netlists that are
        compatible with 7-Series Xilinx devices.
        
            -top <module>
                use the specified module as top module
        
            -family <family>
                run synthesis for the specified Xilinx architecture
                generate the synthesis netlist for the specified family.
                supported values:
                - xcup: Ultrascale Plus
                - xcu: Ultrascale
                - xc7: Series 7 (default)
                - xc6s: Spartan 6
                - xc6v: Virtex 6
                - xc5v: Virtex 5 (EXPERIMENTAL)
                - xc4v: Virtex 4 (EXPERIMENTAL)
                - xc3sda: Spartan 3A DSP (EXPERIMENTAL)
                - xc3sa: Spartan 3A (EXPERIMENTAL)
                - xc3se: Spartan 3E (EXPERIMENTAL)
                - xc3s: Spartan 3 (EXPERIMENTAL)
                - xc2vp: Virtex 2 Pro (EXPERIMENTAL)
                - xc2v: Virtex 2 (EXPERIMENTAL)
                - xcve: Virtex E, Spartan 2E (EXPERIMENTAL)
                - xcv: Virtex, Spartan 2 (EXPERIMENTAL)
        
            -edif <file>
                write the design to the specified edif file. writing of an output file
                is omitted if this parameter is not specified.
        
            -blif <file>
                write the design to the specified BLIF file. writing of an output file
                is omitted if this parameter is not specified.
        
            -ise
                generate an output netlist suitable for ISE
        
            -nobram
                do not use block RAM cells in output netlist
        
            -nolutram
                do not use distributed RAM cells in output netlist
        
            -nosrl
                do not use distributed SRL cells in output netlist
        
            -nocarry
                do not use XORCY/MUXCY/CARRY4 cells in output netlist
        
            -nowidelut
                do not use MUXF[5-9] resources to implement LUTs larger than native for
                the target
        
            -nodsp
                do not use DSP48*s to implement multipliers and associated logic
        
            -noiopad
                disable I/O buffer insertion (useful for hierarchical or 
                out-of-context flows)
        
            -noclkbuf
                disable automatic clock buffer insertion
        
            -uram
                infer URAM288s for large memories (xcup only)
        
            -widemux <int>
                enable inference of hard multiplexer resources (MUXF[78]) for muxes at
                or above this number of inputs (minimum value 2, recommended value >= 5)
                default: 0 (no inference)
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -flatten
                flatten design before synthesis
        
            -dff
                run 'abc'/'abc9' with -dff option
        
            -retime
                run 'abc' with '-D 1' option to enable flip-flop retiming.
                implies -dff.
        
            -abc9
                use new ABC9 flow (EXPERIMENTAL)
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -specify +/xilinx/cells_sim.v
                read_verilog -lib +/xilinx/cells_xtra.v
                hierarchy -check -auto-top
        
            prepare:
                proc
                flatten    (with '-flatten')
                tribuf -logic
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm
                opt
                wreduce [-keepdc]    (option for '-widemux')
                peepopt
                opt_clean
                muxpack        ('-widemux' only)
                pmux2shiftx    (skip if '-nosrl' and '-widemux=0')
                clean          (skip if '-nosrl' and '-widemux=0')
        
            map_dsp:    (skip if '-nodsp')
                memory_dff
                techmap -map +/mul2dsp.v -map +/xilinx/{family}_dsp_map.v {options}
                select a:mul2dsp
                setattr -unset mul2dsp
                opt_expr -fine
                wreduce
                select -clear
                xilinx_dsp -family <family>
                chtype -set $mul t:$__soft_mul
        
            coarse:
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v -D LUT_WIDTH=[46]
                alumacc
                share
                opt
                memory -nomap
                opt_clean
        
            map_memory:
                memory_libmap [...]
                techmap -map +/xilinx/lutrams_<family>_map.v
                techmap -map +/xilinx/brams_<family>_map.v
        
            map_ffram:
                opt -fast -full
                memory_map
        
            fine:
                simplemap t:$mux    ('-widemux' only)
                muxcover <internal options>    ('-widemux' only)
                opt -full
                xilinx_srl -variable -minlen 3    (skip if '-nosrl')
                techmap  -map +/techmap.v -D LUT_SIZE=[46] [-map +/xilinx/mux_map.v] -map +/xilinx/arith_map.v
                opt -fast
        
            map_cells:
                iopadmap -bits -outpad OBUF I:O -inpad IBUF O:I -toutpad OBUFT ~T:I:O -tinoutpad IOBUF ~T:O:I:IO A:top    (skip if '-noiopad')
                techmap -map +/techmap.v -map +/xilinx/cells_map.v
                clean
        
            map_ffs:
                dfflegalize -cell $_DFFE_?P?P_ 01 -cell $_SDFFE_?P?P_ 01 -cell $_DLATCH_?P?_ 01    (for xc6v, xc7, xcu, xcup)
                zinit -all w:* t:$_SDFFE_*    ('-dff' only)
                techmap -map +/xilinx/ff_map.v    ('-abc9' only)
        
            map_luts:
                opt_expr -mux_undef -noclkinv
                abc -luts 2:2,3,6:5[,10,20] [-dff] [-D 1]    (option for '-nowidelut', '-dff', '-retime')
                clean
                techmap -map +/xilinx/ff_map.v    (only if not '-abc9')
                xilinx_srl -fixed -minlen 3    (skip if '-nosrl')
                techmap -map +/xilinx/lut_map.v -map +/xilinx/cells_map.v -D LUT_WIDTH=[46]
                xilinx_dffopt [-lut4]
                opt_lut_ins -tech xilinx
        
            finalize:
                clkbufmap -buf BUFG O:I    (skip if '-noclkbuf')
                extractinv -inv INV O:I    (only if '-ise')
                clean
        
            check:
                hierarchy -check
                stat -tech xilinx
                check -noinit
                blackbox =A:whitebox
        
            edif:
                write_edif -pvector bra 
        
            blif:
                write_blif 
        
