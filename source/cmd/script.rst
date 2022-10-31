===========================================
script - execute commands from file or wire
===========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help script`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        script <filename> [<from_label>:<to_label>]

   
    .. code:: yoscrypt

        script -scriptwire [selection]

    ::

        This command executes the yosys commands in the specified file (default
        behaviour), or commands embedded in the constant text value connected to the
        selected wires.

        In the default (file) case, the 2nd argument can be used to only execute the
        section of the file between the specified labels. An empty from label is
        synonymous with the beginning of the file and an empty to label is synonymous
        with the end of the file.

        If only one label is specified (without ':') then only the block
        marked with that label (until the next label) is executed.

        In "-scriptwire" mode, the commands on the selected wire(s) will be executed
        in the scope of (and thus, relative to) the wires' owning module(s). This
        '-module' mode can be exited by using the 'cd' command.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            script <filename> [<from_label>:<to_label>]
            script -scriptwire [selection]
        
        This command executes the yosys commands in the specified file (default
        behaviour), or commands embedded in the constant text value connected to the
        selected wires.
        
        In the default (file) case, the 2nd argument can be used to only execute the
        section of the file between the specified labels. An empty from label is
        synonymous with the beginning of the file and an empty to label is synonymous
        with the end of the file.
        
        If only one label is specified (without ':') then only the block
        marked with that label (until the next label) is executed.
        
        In "-scriptwire" mode, the commands on the selected wire(s) will be executed
        in the scope of (and thus, relative to) the wires' owning module(s). This
        '-module' mode can be exited by using the 'cd' command.
        
