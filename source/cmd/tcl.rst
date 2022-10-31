===============================
tcl - execute a TCL script file
===============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help tcl`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        tcl <filename> [args]

    ::

        This command executes the tcl commands in the specified file.
        Use 'yosys cmd' to run the yosys command 'cmd' from tcl.

        The tcl command 'yosys -import' can be used to import all yosys
        commands directly as tcl commands to the tcl shell. Yosys commands
        'proc' and 'rename' are wrapped to tcl commands 'procs' and 'renames'
        in order to avoid a name collision with the built in commands.

        If any arguments are specified, these arguments are provided to the script via
        the standard $argc and $argv variables.

        Note, tcl will not recieve the output of any yosys command. If the output
        of the tcl commands are needed, use the yosys command 'tee' to redirect yosys's
        output to a temporary file.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            tcl <filename> [args]
        
        This command executes the tcl commands in the specified file.
        Use 'yosys cmd' to run the yosys command 'cmd' from tcl.
        
        The tcl command 'yosys -import' can be used to import all yosys
        commands directly as tcl commands to the tcl shell. Yosys commands
        'proc' and 'rename' are wrapped to tcl commands 'procs' and 'renames'
        in order to avoid a name collision with the built in commands.
        
        If any arguments are specified, these arguments are provided to the script via
        the standard $argc and $argv variables.
        
        Note, tcl will not recieve the output of any yosys command. If the output
        of the tcl commands are needed, use the yosys command 'tee' to redirect yosys's
        output to a temporary file.
        
