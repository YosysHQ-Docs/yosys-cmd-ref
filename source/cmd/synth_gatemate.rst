==========================================================
synth_gatemate - synthesis for Cologne Chip GateMate FPGAs
==========================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth_gatemate`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth_gatemate [options]

    ::

        This command runs synthesis for Cologne Chip AG GateMate FPGAs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module.


    .. code:: yoscrypt

        -vlog <file>

    ::

            write the design to the specified verilog file. Writing of an output
            file is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -json <file>

    ::

            write the design to the specified JSON file. Writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -run <from_label>:<to_label>

    ::

            only run the commands between the labels (see below). An empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -noflatten

    ::

            do not flatten design before synthesis.


    .. code:: yoscrypt

        -nobram

    ::

            do not use CC_BRAM_20K or CC_BRAM_40K cells in output netlist.


    .. code:: yoscrypt

        -noaddf

    ::

            do not use CC_ADDF full adder cells in output netlist.


    .. code:: yoscrypt

        -nomult

    ::

            do not use CC_MULT multiplier cells in output netlist.


    .. code:: yoscrypt

        -nomx8, -nomx4

    ::

            do not use CC_MX{8,4} multiplexer cells in output netlist.


    .. code:: yoscrypt

        -luttree

    ::

            use new LUT tree mapping approach (EXPERIMENTAL).


    .. code:: yoscrypt

        -dff

    ::

            run 'abc' with -dff option


    .. code:: yoscrypt

        -retime

    ::

            run 'abc' with '-dff -D 1' options


    .. code:: yoscrypt

        -noiopad

    ::

            disable I/O buffer insertion (useful for hierarchical or 
            out-of-context flows).


    .. code:: yoscrypt

        -noclkbuf

    ::

            disable automatic clock buffer insertion.


    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib -specify +/gatemate/cells_sim.v +/gatemate/cells_bb.v
                hierarchy -check -top <top>

            prepare:
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
                muxpack
                share
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean

            map_mult:    (skip if '-nomult')
                techmap -map +/gatemate/mul_map.v

            coarse:
                alumacc
                opt
                memory -nomap
                opt_clean

            map_bram:    (skip if '-nobram')
                memory_libmap -lib +/gatemate/brams.txt
                techmap -map +/gatemate/brams_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                techmap -map +/techmap.v  -map +/gatemate/arith_map.v
                opt -fast

            map_io:    (skip if '-noiopad')
                iopadmap -bits -inpad CC_IBUF Y:I -outpad CC_OBUF A:O -toutpad CC_TOBUF ~T:A:O -tinoutpad CC_IOBUF ~T:Y:A:IO
                clean

            map_regs:
                opt_clean
                dfflegalize -cell $_DFFE_????_ 01 -cell $_DLATCH_???_ 01
                techmap -map +/gatemate/reg_map.v
                opt_expr -mux_undef
                simplemap
                opt_clean

            map_muxs:
                muxcover  -mux4 -mux8
                opt -full
                techmap -map +/gatemate/mux_map.v

            map_luts:
                abc  -genlib +/gatemate/lut_tree_cells.genlib    (with -luttree)
                techmap -map +/gatemate/lut_tree_map.v    (with -luttree)
                gatemate_foldinv    (with -luttree)
                techmap -map +/gatemate/inv_map.v    (with -luttree)
                abc  -dress -lut 4    (without -luttree)
                clean

            map_cells:
                techmap -map +/gatemate/lut_map.v
                clean

            map_bufg:    (skip if '-noclkbuf')
                clkbufmap -buf CC_BUFG O:I
                clean

            check:
                hierarchy -check
                stat -width
                check -noinit
                blackbox =A:whitebox

            vlog:
                opt_clean -purge
                write_verilog -noattr <file-name>

            json:
                write_json <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_gatemate [options]
        
        This command runs synthesis for Cologne Chip AG GateMate FPGAs.
        
            -top <module>
                use the specified module as top module.
        
            -vlog <file>
                write the design to the specified verilog file. Writing of an output
                file is omitted if this parameter is not specified.
        
            -json <file>
                write the design to the specified JSON file. Writing of an output file
                is omitted if this parameter is not specified.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). An empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -noflatten
                do not flatten design before synthesis.
        
            -nobram
                do not use CC_BRAM_20K or CC_BRAM_40K cells in output netlist.
        
            -noaddf
                do not use CC_ADDF full adder cells in output netlist.
        
            -nomult
                do not use CC_MULT multiplier cells in output netlist.
        
            -nomx8, -nomx4
                do not use CC_MX{8,4} multiplexer cells in output netlist.
        
            -luttree
                use new LUT tree mapping approach (EXPERIMENTAL).
        
            -dff
                run 'abc' with -dff option
        
            -retime
                run 'abc' with '-dff -D 1' options
        
            -noiopad
                disable I/O buffer insertion (useful for hierarchical or 
                out-of-context flows).
        
            -noclkbuf
                disable automatic clock buffer insertion.
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -specify +/gatemate/cells_sim.v +/gatemate/cells_bb.v
                hierarchy -check -top <top>
        
            prepare:
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
                muxpack
                share
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean
        
            map_mult:    (skip if '-nomult')
                techmap -map +/gatemate/mul_map.v
        
            coarse:
                alumacc
                opt
                memory -nomap
                opt_clean
        
            map_bram:    (skip if '-nobram')
                memory_libmap -lib +/gatemate/brams.txt
                techmap -map +/gatemate/brams_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                techmap -map +/techmap.v  -map +/gatemate/arith_map.v
                opt -fast
        
            map_io:    (skip if '-noiopad')
                iopadmap -bits -inpad CC_IBUF Y:I -outpad CC_OBUF A:O -toutpad CC_TOBUF ~T:A:O -tinoutpad CC_IOBUF ~T:Y:A:IO
                clean
        
            map_regs:
                opt_clean
                dfflegalize -cell $_DFFE_????_ 01 -cell $_DLATCH_???_ 01
                techmap -map +/gatemate/reg_map.v
                opt_expr -mux_undef
                simplemap
                opt_clean
        
            map_muxs:
                muxcover  -mux4 -mux8
                opt -full
                techmap -map +/gatemate/mux_map.v
        
            map_luts:
                abc  -genlib +/gatemate/lut_tree_cells.genlib    (with -luttree)
                techmap -map +/gatemate/lut_tree_map.v    (with -luttree)
                gatemate_foldinv    (with -luttree)
                techmap -map +/gatemate/inv_map.v    (with -luttree)
                abc  -dress -lut 4    (without -luttree)
                clean
        
            map_cells:
                techmap -map +/gatemate/lut_map.v
                clean
        
            map_bufg:    (skip if '-noclkbuf')
                clkbufmap -buf CC_BUFG O:I
                clean
        
            check:
                hierarchy -check
                stat -width
                check -noinit
                blackbox =A:whitebox
        
            vlog:
                opt_clean -purge
                write_verilog -noattr <file-name>
        
            json:
                write_json <file-name>
        
