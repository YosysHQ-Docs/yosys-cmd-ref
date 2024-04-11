====================================
write_smv - write design to SMV file
====================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: write_smv
    :title: write design to SMV file



    .. code:: yoscrypt

        write_smv [options] [filename]

    ::

        Write an SMV description of the current design.


    .. code:: yoscrypt

        -verbose

    ::

            this will print the recursive walk used to export the modules.


    .. code:: yoscrypt

        -tpl <template_file>

    ::

            use the given template file. the line containing only the token '%%'
            is replaced with the regular output of this command.


    ::

        THIS COMMAND IS UNDER CONSTRUCTION

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_smv [options] [filename]
        
        Write an SMV description of the current design.
        
            -verbose
                this will print the recursive walk used to export the modules.
        
            -tpl <template_file>
                use the given template file. the line containing only the token '%%'
                is replaced with the regular output of this command.
        
        THIS COMMAND IS UNDER CONSTRUCTION
        
