======================================
shell - enter interactive command mode
======================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: shell
    :title: enter interactive command mode



    .. code:: yoscrypt

        shell

    ::

        This command enters the interactive command mode. This can be useful
        in a script to interrupt the script at a certain point and allow for
        interactive inspection or manual synthesis of the design at this point.

        The command prompt of the interactive shell indicates the current
        selection (see 'help select'):

            yosys>
                the entire design is selected

            yosys*>
                only part of the design is selected

            yosys [modname]>
                the entire module 'modname' is selected using 'select -module modname'

            yosys [modname]*>
                only part of current module 'modname' is selected

        When in interactive shell, some errors (e.g. invalid command arguments)
        do not terminate yosys but return to the command prompt.

        This command is the default action if nothing else has been specified
        on the command line.

        Press Ctrl-D or type 'exit' to leave the interactive shell.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            shell
        
        This command enters the interactive command mode. This can be useful
        in a script to interrupt the script at a certain point and allow for
        interactive inspection or manual synthesis of the design at this point.
        
        The command prompt of the interactive shell indicates the current
        selection (see 'help select'):
        
            yosys>
                the entire design is selected
        
            yosys*>
                only part of the design is selected
        
            yosys [modname]>
                the entire module 'modname' is selected using 'select -module modname'
        
            yosys [modname]*>
                only part of current module 'modname' is selected
        
        When in interactive shell, some errors (e.g. invalid command arguments)
        do not terminate yosys but return to the command prompt.
        
        This command is the default action if nothing else has been specified
        on the command line.
        
        Press Ctrl-D or type 'exit' to leave the interactive shell.
        
