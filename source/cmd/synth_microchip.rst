===============================================
synth_microchip - synthesis for Microchip FPGAs
===============================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_microchip
    :title: synthesis for Microchip FPGAs



    .. code:: yoscrypt

        synth_microchip [options]

    ::

        This command runs synthesis for Microchip FPGAs. This command creates 
        netlists that are compatible with Microchip PolarFire devices. 


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as the top module


    .. code:: yoscrypt

        -family <family>

    ::

            Run synthesis for the specified Microchip architecture. 
            Generate the synthesis netlist for the specified family.
            supported values:
            - polarfire: PolarFire


    .. code:: yoscrypt

        -edif <file>

    ::

            Write the design to the specified edif file. Writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -blif <file>

    ::

            Write the design to the specified BLIF file. Writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -vlog <file>

    ::

            write the design to the specified Verilog file. writing of an output
            file is omitted if this parameter is not specified.

    ::

        -nobram
            Do not use block RAM cells in output netlist


    .. code:: yoscrypt

        -nocarry

    ::

            Do not use ARI1 cells in output netlist


    .. code:: yoscrypt

        -nodsp

    ::

            Do not use MATH blocks to implement multipliers and associated logic


    .. code:: yoscrypt

        -noiopad

    ::

            Disable I/O buffer insertion (useful for hierarchical or 
            out-of-context flows)


    .. code:: yoscrypt

        -noclkbuf

    ::

            Disable automatic clock buffer insertion


    .. code:: yoscrypt

        -run <from_label>:<to_label>

    ::

            Only run the commands between the labels (see below). an empty
            'from_label' is synonymous to 'begin', and empty 'to_label' is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -noflatten

    ::

            do not flatten design before synthesis


    .. code:: yoscrypt

        -dff

    ::

            Run 'abc'/'abc9' with -dff option


    .. code:: yoscrypt

        -retime

    ::

            Run 'abc' with '-D 1' option to enable flip-flop retiming.
            implies -dff.


    .. code:: yoscrypt

        -noabc9

    ::

            Use classic ABC flow instead of ABC9


    .. code:: yoscrypt

        -discard-ffinit

    ::

            discard FF init value instead of emitting an error



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib -specify +/microchip/cells_sim.v
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
                wreduce
                peepopt
                opt_clean

            map_dsp:    (skip if '-nodsp')
                memory_dff
                techmap -map +/mul2dsp.v -map +/microchip/{family}_dsp_map.v {options}
                select a:mul2dsp
                setattr -unset mul2dsp
                opt_expr -fine
                wreduce
                select -clear
                microchip_dsp -family <family>
                chtype -set $mul t:$__soft_mul

            coarse:
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v -D LUT_WIDTH=[4]
                alumacc
                share
                opt
                memory -nomap
                opt_clean
                attrmap -remove init    (only if -discard-ffinit)

            map_memory:
                memory_libmap [...]
                techmap -map +/microchip/LSRAM_map.v
                techmap -map +/microchip/uSRAM_map.v

            map_ffram:
                opt -fast -full
                memory_map

            fine:
                opt -full
                simplemap t:$mux
                simplemap t:$xor
                extract_reduce
                muxcover -nodecode -mux4=220
                techmap -map +/microchip/arith_map.v
                techmap -map +/techmap.v
                opt -fast

            map_cells:
                iopadmap -bits -inpad INBUF Y:PAD -outpad OUTBUF D:PAD -toutpad TRIBUFF E:D:PAD -tinoutpad BIBUF E:Y:D:PAD    (unless -noiobs)
                techmap -map +/techmap.v -map +/microchip/cells_map.v
                clean

            map_ffs:
                dfflegalize -cell $_DFFE_PN?P_ x -cell $_SDFFCE_PN?P_ x -cell $_DLATCH_PN?_ x    (Converts FFs to supported types)
                zinit -all w:* t:$_SDFFCE_*    ('-dff' only)
                techmap -D NO_LUT -map +/microchip/cells_map.v    ('-abc9' only)

            map_luts:
                opt_expr -mux_undef -noclkinv
                abc -luts 2:2,3,6:5[,10,20] [-dff] [-D 1]    (option for '-nowidelut', '-dff', '-retime')
                clean
                techmap -D NO_LUT -map +/microchip/cells_map.v    (only if not '-abc9')
                techmap -map +/microchip/cells_map.v -D FINAL_MAP -D LUT_WIDTH=[4]
                microchip_dffopt
                clkbufmap -buf CLKINT Y:A -inpad CLKBUF Y:PAD
                clean -purge

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            edif:
                write_edif -pvector bra 

            blif:
                write_blif 

            vlog:
                write_verilog <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_microchip [options]
        
        This command runs synthesis for Microchip FPGAs. This command creates 
        netlists that are compatible with Microchip PolarFire devices. 
        
            -top <module>
                use the specified module as the top module
        
            -family <family>
                Run synthesis for the specified Microchip architecture. 
                Generate the synthesis netlist for the specified family.
                supported values:
                - polarfire: PolarFire
        
            -edif <file>
                Write the design to the specified edif file. Writing of an output file
                is omitted if this parameter is not specified.
        
            -blif <file>
                Write the design to the specified BLIF file. Writing of an output file
                is omitted if this parameter is not specified.
        
            -vlog <file>
                write the design to the specified Verilog file. writing of an output
                file is omitted if this parameter is not specified.
            -nobram
                Do not use block RAM cells in output netlist
        
            -nocarry
                Do not use ARI1 cells in output netlist
        
            -nodsp
                Do not use MATH blocks to implement multipliers and associated logic
        
            -noiopad
                Disable I/O buffer insertion (useful for hierarchical or 
                out-of-context flows)
        
            -noclkbuf
                Disable automatic clock buffer insertion
        
            -run <from_label>:<to_label>
                Only run the commands between the labels (see below). an empty
                'from_label' is synonymous to 'begin', and empty 'to_label' is
                synonymous to the end of the command list.
        
            -noflatten
                do not flatten design before synthesis
        
            -dff
                Run 'abc'/'abc9' with -dff option
        
            -retime
                Run 'abc' with '-D 1' option to enable flip-flop retiming.
                implies -dff.
        
            -noabc9
                Use classic ABC flow instead of ABC9
        
            -discard-ffinit
                discard FF init value instead of emitting an error
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -specify +/microchip/cells_sim.v
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
                wreduce
                peepopt
                opt_clean
        
            map_dsp:    (skip if '-nodsp')
                memory_dff
                techmap -map +/mul2dsp.v -map +/microchip/{family}_dsp_map.v {options}
                select a:mul2dsp
                setattr -unset mul2dsp
                opt_expr -fine
                wreduce
                select -clear
                microchip_dsp -family <family>
                chtype -set $mul t:$__soft_mul
        
            coarse:
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v -D LUT_WIDTH=[4]
                alumacc
                share
                opt
                memory -nomap
                opt_clean
                attrmap -remove init    (only if -discard-ffinit)
        
            map_memory:
                memory_libmap [...]
                techmap -map +/microchip/LSRAM_map.v
                techmap -map +/microchip/uSRAM_map.v
        
            map_ffram:
                opt -fast -full
                memory_map
        
            fine:
                opt -full
                simplemap t:$mux
                simplemap t:$xor
                extract_reduce
                muxcover -nodecode -mux4=220
                techmap -map +/microchip/arith_map.v
                techmap -map +/techmap.v
                opt -fast
        
            map_cells:
                iopadmap -bits -inpad INBUF Y:PAD -outpad OUTBUF D:PAD -toutpad TRIBUFF E:D:PAD -tinoutpad BIBUF E:Y:D:PAD    (unless -noiobs)
                techmap -map +/techmap.v -map +/microchip/cells_map.v
                clean
        
            map_ffs:
                dfflegalize -cell $_DFFE_PN?P_ x -cell $_SDFFCE_PN?P_ x -cell $_DLATCH_PN?_ x    (Converts FFs to supported types)
                zinit -all w:* t:$_SDFFCE_*    ('-dff' only)
                techmap -D NO_LUT -map +/microchip/cells_map.v    ('-abc9' only)
        
            map_luts:
                opt_expr -mux_undef -noclkinv
                abc -luts 2:2,3,6:5[,10,20] [-dff] [-D 1]    (option for '-nowidelut', '-dff', '-retime')
                clean
                techmap -D NO_LUT -map +/microchip/cells_map.v    (only if not '-abc9')
                techmap -map +/microchip/cells_map.v -D FINAL_MAP -D LUT_WIDTH=[4]
                microchip_dffopt
                clkbufmap -buf CLKINT Y:A -inpad CLKBUF Y:PAD
                clean -purge
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            edif:
                write_edif -pvector bra 
        
            blif:
                write_blif 
        
            vlog:
                write_verilog <file-name>
        
