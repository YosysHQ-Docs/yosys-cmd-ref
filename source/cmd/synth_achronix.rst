===========================================================
synth_achronix - synthesis for Acrhonix Speedster22i FPGAs.
===========================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth_achronix`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth_achronix [options]

    ::

        This command runs synthesis for Achronix Speedster eFPGAs. This work is still experimental.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module (default='top')


    .. code:: yoscrypt

        -vout <file>

    ::

            write the design to the specified Verilog netlist file. writing of an
            output file is omitted if this parameter is not specified.


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



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -sv -lib +/achronix/speedster22i/cells_sim.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout

            coarse:
                synth -run coarse

            fine:
                opt -fast -mux_undef -undriven -fine -full
                memory_map
                opt -undriven -fine
                opt -fine
                techmap -map +/techmap.v
                opt -full
                clean -purge
                setundef -undriven -zero
                dfflegalize -cell $_DFF_P_ x
                abc -markgroups -dff -D 1    (only if -retime)

            map_luts:
                abc -lut 4
                clean

            map_cells:
                iopadmap -bits -outpad $__outpad I:O -inpad $__inpad O:I
                techmap -map +/achronix/speedster22i/cells_map.v
                clean -purge

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            vout:
                write_verilog -nodec -attr2comment -defparam -renameprefix syn_ <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_achronix [options]
        
        This command runs synthesis for Achronix Speedster eFPGAs. This work is still experimental.
        
            -top <module>
                use the specified module as top module (default='top')
        
            -vout <file>
                write the design to the specified Verilog netlist file. writing of an
                output file is omitted if this parameter is not specified.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -noflatten
                do not flatten design before synthesis
        
            -retime
                run 'abc' with '-dff -D 1' options
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -sv -lib +/achronix/speedster22i/cells_sim.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout
        
            coarse:
                synth -run coarse
        
            fine:
                opt -fast -mux_undef -undriven -fine -full
                memory_map
                opt -undriven -fine
                opt -fine
                techmap -map +/techmap.v
                opt -full
                clean -purge
                setundef -undriven -zero
                dfflegalize -cell $_DFF_P_ x
                abc -markgroups -dff -D 1    (only if -retime)
        
            map_luts:
                abc -lut 4
                clean
        
            map_cells:
                iopadmap -bits -outpad $__outpad I:O -inpad $__inpad O:I
                techmap -map +/achronix/speedster22i/cells_map.v
                clean -purge
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            vout:
                write_verilog -nodec -attr2comment -defparam -renameprefix syn_ <file-name>
        
