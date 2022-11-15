=============================
bugpoint - minimize testcases
=============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help bugpoint`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        bugpoint [options] [-script <filename> | -command "<command>"]

    ::

        This command minimizes the current design that is known to crash Yosys with the
        given script into a smaller testcase. It does this by removing an arbitrary part
        of the design and recursively invokes a new Yosys process with this modified
        design and the same script, repeating these steps while it can find a smaller
        design that still causes a crash. Once this command finishes, it replaces the
        current design with the smallest testcase it was able to produce.
        In order to save the reduced testcase you must write this out to a file with
        another command after `bugpoint` like `write_rtlil` or `write_verilog`.


    .. code:: yoscrypt

        -script <filename> | -command "<command>"

    ::

            use this script file or command to crash Yosys. required.


    .. code:: yoscrypt

        -yosys <filename>

    ::

            use this Yosys binary. if not specified, `yosys` is used.


    .. code:: yoscrypt

        -grep "<string>"

    ::

            only consider crashes that place this string in the log file.


    .. code:: yoscrypt

        -fast

    ::

            run `proc_clean; clean -purge` after each minimization step. converges
            faster, but produces larger testcases, and may fail to produce any
            testcase at all if the crash is related to dangling wires.


    .. code:: yoscrypt

        -clean

    ::

            run `proc_clean; clean -purge` before checking testcase and after
            finishing. produces smaller and more useful testcases, but may fail to
            produce any testcase at all if the crash is related to dangling wires.


    ::

        It is possible to constrain which parts of the design will be considered for
        removal. Unless one or more of the following options are specified, all parts
        will be considered.


    .. code:: yoscrypt

        -modules

    ::

            try to remove modules. modules with a (* bugpoint_keep *) attribute
            will be skipped.


    .. code:: yoscrypt

        -ports

    ::

            try to remove module ports. ports with a (* bugpoint_keep *) attribute
            will be skipped (useful for clocks, resets, etc.)


    .. code:: yoscrypt

        -cells

    ::

            try to remove cells. cells with a (* bugpoint_keep *) attribute will
            be skipped.


    .. code:: yoscrypt

        -connections

    ::

            try to reconnect ports to 'x.


    .. code:: yoscrypt

        -processes

    ::

            try to remove processes. processes with a (* bugpoint_keep *) attribute
            will be skipped.


    .. code:: yoscrypt

        -assigns

    ::

            try to remove process assigns from cases.


    .. code:: yoscrypt

        -updates

    ::

            try to remove process updates from syncs.


    .. code:: yoscrypt

        -runner "<prefix>"

    ::

            child process wrapping command, e.g., "timeout 30", or valgrind.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            bugpoint [options] [-script <filename> | -command "<command>"]
        
        This command minimizes the current design that is known to crash Yosys with the
        given script into a smaller testcase. It does this by removing an arbitrary part
        of the design and recursively invokes a new Yosys process with this modified
        design and the same script, repeating these steps while it can find a smaller
        design that still causes a crash. Once this command finishes, it replaces the
        current design with the smallest testcase it was able to produce.
        In order to save the reduced testcase you must write this out to a file with
        another command after `bugpoint` like `write_rtlil` or `write_verilog`.
        
            -script <filename> | -command "<command>"
                use this script file or command to crash Yosys. required.
        
            -yosys <filename>
                use this Yosys binary. if not specified, `yosys` is used.
        
            -grep "<string>"
                only consider crashes that place this string in the log file.
        
            -fast
                run `proc_clean; clean -purge` after each minimization step. converges
                faster, but produces larger testcases, and may fail to produce any
                testcase at all if the crash is related to dangling wires.
        
            -clean
                run `proc_clean; clean -purge` before checking testcase and after
                finishing. produces smaller and more useful testcases, but may fail to
                produce any testcase at all if the crash is related to dangling wires.
        
        It is possible to constrain which parts of the design will be considered for
        removal. Unless one or more of the following options are specified, all parts
        will be considered.
        
            -modules
                try to remove modules. modules with a (* bugpoint_keep *) attribute
                will be skipped.
        
            -ports
                try to remove module ports. ports with a (* bugpoint_keep *) attribute
                will be skipped (useful for clocks, resets, etc.)
        
            -cells
                try to remove cells. cells with a (* bugpoint_keep *) attribute will
                be skipped.
        
            -connections
                try to reconnect ports to 'x.
        
            -processes
                try to remove processes. processes with a (* bugpoint_keep *) attribute
                will be skipped.
        
            -assigns
                try to remove process assigns from cases.
        
            -updates
                try to remove process updates from syncs.
        
            -runner "<prefix>"
                child process wrapping command, e.g., "timeout 30", or valgrind.
        
