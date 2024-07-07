=========================================
synth_efinix - synthesis for Efinix FPGAs
=========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_efinix
    :title: synthesis for Efinix FPGAs



    .. code:: yoscrypt

        synth_efinix [options]

    ::

        This command runs synthesis for Efinix FPGAs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module


    .. code:: yoscrypt

        -edif <file>

    ::

            write the design to the specified EDIF file. writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -json <file>

    ::

            write the design to the specified JSON file. writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -run <from_label>:<to_label>

    ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -noflatten

    ::

            do not flatten design before synthesis


    .. code:: yoscrypt

        -retime

    ::

            run 'abc' with '-dff -D 1' options


    .. code:: yoscrypt

        -nobram

    ::

            do not use EFX_RAM_5K cells in output netlist



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib +/efinix/cells_sim.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout

            coarse:
                synth -run coarse

            map_ram:
                memory_libmap -lib +/efinix/brams.txt [-no-auto-block]    (-no-auto-block if -nobram)
                techmap -map +/efinix/brams_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                techmap -map +/techmap.v -map +/efinix/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)

            map_ffs:
                dfflegalize -cell $_DFFE_????_ 0 -cell $_SDFFE_????_ 0 -cell $_SDFFCE_????_ 0 -cell $_DLATCH_?_ x
                techmap -D NO_LUT -map +/efinix/cells_map.v
                opt_expr -mux_undef
                simplemap

            map_luts:
                abc -lut 4
                clean

            map_cells:
                techmap -map +/efinix/cells_map.v
                clean

            map_gbuf:
                clkbufmap -buf $__EFX_GBUF O:I
                techmap -map +/efinix/gbuf_map.v
                efinix_fixcarry
                clean

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            edif:
                write_edif <file-name>

            json:
                write_json <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_efinix [options]
        
        This command runs synthesis for Efinix FPGAs.
        
            -top <module>
                use the specified module as top module
        
            -edif <file>
                write the design to the specified EDIF file. writing of an output file
                is omitted if this parameter is not specified.
        
            -json <file>
                write the design to the specified JSON file. writing of an output file
                is omitted if this parameter is not specified.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -noflatten
                do not flatten design before synthesis
        
            -retime
                run 'abc' with '-dff -D 1' options
        
            -nobram
                do not use EFX_RAM_5K cells in output netlist
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib +/efinix/cells_sim.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout
        
            coarse:
                synth -run coarse
        
            map_ram:
                memory_libmap -lib +/efinix/brams.txt [-no-auto-block]    (-no-auto-block if -nobram)
                techmap -map +/efinix/brams_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                techmap -map +/techmap.v -map +/efinix/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
        
            map_ffs:
                dfflegalize -cell $_DFFE_????_ 0 -cell $_SDFFE_????_ 0 -cell $_SDFFCE_????_ 0 -cell $_DLATCH_?_ x
                techmap -D NO_LUT -map +/efinix/cells_map.v
                opt_expr -mux_undef
                simplemap
        
            map_luts:
                abc -lut 4
                clean
        
            map_cells:
                techmap -map +/efinix/cells_map.v
                clean
        
            map_gbuf:
                clkbufmap -buf $__EFX_GBUF O:I
                techmap -map +/efinix/gbuf_map.v
                efinix_fixcarry
                clean
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            edif:
                write_edif <file-name>
        
            json:
                write_json <file-name>
        
