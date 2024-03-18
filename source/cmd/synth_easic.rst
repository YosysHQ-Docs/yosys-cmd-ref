==========================================
synth_easic - synthesis for eASIC platform
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_easic
    :title: synthesis for eASIC platform



    .. code:: yoscrypt

        synth_easic [options]

    ::

        This command runs synthesis for eASIC platform.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module


    .. code:: yoscrypt

        -vlog <file>

    ::

            write the design to the specified structural Verilog file. writing of
            an output file is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -etools <path>

    ::

            set path to the eTools installation. (default=/opt/eTools)


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
                read_liberty -lib <etools_phys_clk_lib>
                read_liberty -lib <etools_logic_lut_lib>
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten

            coarse:
                synth -run coarse

            fine:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
                techmap
                opt -fast
                abc -dff -D 1     (only if -retime)
                opt_clean    (only if -retime)

            map:
                dfflibmap -liberty <etools_phys_clk_lib>
                abc -liberty <etools_logic_lut_lib>
                opt_clean

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            vlog:
                write_verilog -noexpr -attr2comment <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_easic [options]
        
        This command runs synthesis for eASIC platform.
        
            -top <module>
                use the specified module as top module
        
            -vlog <file>
                write the design to the specified structural Verilog file. writing of
                an output file is omitted if this parameter is not specified.
        
            -etools <path>
                set path to the eTools installation. (default=/opt/eTools)
        
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
                read_liberty -lib <etools_phys_clk_lib>
                read_liberty -lib <etools_logic_lut_lib>
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
        
            coarse:
                synth -run coarse
        
            fine:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
                techmap
                opt -fast
                abc -dff -D 1     (only if -retime)
                opt_clean    (only if -retime)
        
            map:
                dfflibmap -liberty <etools_phys_clk_lib>
                abc -liberty <etools_logic_lut_lib>
                opt_clean
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            vlog:
                write_verilog -noexpr -attr2comment <file-name>
        
