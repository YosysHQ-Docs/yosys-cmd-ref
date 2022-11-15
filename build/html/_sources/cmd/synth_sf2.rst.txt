=======================================================
synth_sf2 - synthesis for SmartFusion2 and IGLOO2 FPGAs
=======================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth_sf2`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth_sf2 [options]

    ::

        This command runs synthesis for SmartFusion2 and IGLOO2 FPGAs.


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

        -vlog <file>

    ::

            write the design to the specified Verilog file. writing of an output
            file is omitted if this parameter is not specified.


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

        -noiobs

    ::

            run synthesis in "block mode", i.e. do not insert IO buffers


    .. code:: yoscrypt

        -clkbuf

    ::

            insert direct PAD->global_net buffers


    .. code:: yoscrypt

        -discard-ffinit

    ::

            discard FF init value instead of emitting an error


    .. code:: yoscrypt

        -retime

    ::

            run 'abc' with '-dff -D 1' options



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib +/sf2/cells_sim.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout

            coarse:
                attrmap -remove init    (only if -discard-ffinit)
                synth -run coarse

            fine:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
                techmap -map +/techmap.v -map +/sf2/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)

            map_ffs:
                dfflegalize -cell $_DFFE_PN?P_ x -cell $_SDFFCE_PN?P_ x -cell $_DLATCH_PN?_ x
                techmap -D NO_LUT -map +/sf2/cells_map.v
                opt_expr -mux_undef
                simplemap

            map_luts:
                abc -lut 4
                clean

            map_cells:
                techmap -map +/sf2/cells_map.v
                clean

            map_iobs:
                clkbufmap -buf CLKINT Y:A [-inpad CLKBUF Y:PAD]    (unless -noiobs, -inpad only passed if -clkbuf)
                iopadmap -bits -inpad INBUF Y:PAD -outpad OUTBUF D:PAD -toutpad TRIBUFF E:D:PAD -tinoutpad BIBUF E:Y:D:PAD    (unless -noiobs)
                clean -purge

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            edif:
                write_edif -gndvccy <file-name>

            vlog:
                write_verilog <file-name>

            json:
                write_json <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_sf2 [options]
        
        This command runs synthesis for SmartFusion2 and IGLOO2 FPGAs.
        
            -top <module>
                use the specified module as top module
        
            -edif <file>
                write the design to the specified EDIF file. writing of an output file
                is omitted if this parameter is not specified.
        
            -vlog <file>
                write the design to the specified Verilog file. writing of an output
                file is omitted if this parameter is not specified.
        
            -json <file>
                write the design to the specified JSON file. writing of an output file
                is omitted if this parameter is not specified.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -noflatten
                do not flatten design before synthesis
        
            -noiobs
                run synthesis in "block mode", i.e. do not insert IO buffers
        
            -clkbuf
                insert direct PAD->global_net buffers
        
            -discard-ffinit
                discard FF init value instead of emitting an error
        
            -retime
                run 'abc' with '-dff -D 1' options
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib +/sf2/cells_sim.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout
        
            coarse:
                attrmap -remove init    (only if -discard-ffinit)
                synth -run coarse
        
            fine:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
                techmap -map +/techmap.v -map +/sf2/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
        
            map_ffs:
                dfflegalize -cell $_DFFE_PN?P_ x -cell $_SDFFCE_PN?P_ x -cell $_DLATCH_PN?_ x
                techmap -D NO_LUT -map +/sf2/cells_map.v
                opt_expr -mux_undef
                simplemap
        
            map_luts:
                abc -lut 4
                clean
        
            map_cells:
                techmap -map +/sf2/cells_map.v
                clean
        
            map_iobs:
                clkbufmap -buf CLKINT Y:A [-inpad CLKBUF Y:PAD]    (unless -noiobs, -inpad only passed if -clkbuf)
                iopadmap -bits -inpad INBUF Y:PAD -outpad OUTBUF D:PAD -toutpad TRIBUFF E:D:PAD -tinoutpad BIBUF E:Y:D:PAD    (unless -noiobs)
                clean -purge
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            edif:
                write_edif -gndvccy <file-name>
        
            vlog:
                write_verilog <file-name>
        
            json:
                write_json <file-name>
        
