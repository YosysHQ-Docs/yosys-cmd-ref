==========================================
synth_easic - synthesis for eASIC platform
==========================================

.. only:: html

    :code:`yosys> help synth_easic`
    ----------------------------------------------------------------------------


    :code:`synth_easic [options]` ::

        This command runs synthesis for eASIC platform.


    :code:`-top <module>` ::

            use the specified module as top module


    :code:`-vlog <file>` ::

            write the design to the specified structural Verilog file. writing of
            an output file is omitted if this parameter is not specified.


    :code:`-etools <path>` ::

            set path to the eTools installation. (default=/opt/eTools)


    :code:`-run <from_label>:<to_label>` ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    :code:`-noflatten` ::

            do not flatten design before synthesis


    :code:`-retime` ::

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
        
