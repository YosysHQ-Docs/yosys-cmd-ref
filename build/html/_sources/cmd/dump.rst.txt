================================================
dump - print parts of the design in RTLIL format
================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help dump`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        dump [options] [selection]

    ::

        Write the selected parts of the design to the console or specified file in
        RTLIL format.


    .. code:: yoscrypt

        -m

    ::

            also dump the module headers, even if only parts of a single
            module is selected


    .. code:: yoscrypt

        -n

    ::

            only dump the module headers if the entire module is selected


    .. code:: yoscrypt

        -o <filename>

    ::

            write to the specified file.


    .. code:: yoscrypt

        -a <filename>

    ::

            like -outfile but append instead of overwrite

.. raw:: latex

    \end{comment}

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
        
