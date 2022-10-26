================================================
dump - print parts of the design in RTLIL format
================================================

.. only:: html

    :code:`yosys> help dump`
    ----------------------------------------------------------------------------


    :code:`dump [options] [selection]` ::

        Write the selected parts of the design to the console or specified file in
        RTLIL format.


    :code:`-m` ::

            also dump the module headers, even if only parts of a single
            module is selected


    :code:`-n` ::

            only dump the module headers if the entire module is selected


    :code:`-o <filename>` ::

            write to the specified file.


    :code:`-a <filename>` ::

            like -outfile but append instead of overwrite

.. only:: latex

    ::

        
            dump [options] [selection]
        
        Write the selected parts of the design to the console or specified file in
        RTLIL format.
        
            -m
                also dump the module headers, even if only parts of a single
                module is selected
        
            -n
                only dump the module headers if the entire module is selected
        
            -o <filename>
                write to the specified file.
        
            -a <filename>
                like -outfile but append instead of overwrite
        
