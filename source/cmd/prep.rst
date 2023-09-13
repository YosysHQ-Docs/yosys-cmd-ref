===============================
prep - generic synthesis script
===============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help prep`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        prep [options]

    ::

        This command runs a conservative RTL synthesis. A typical application for this
        is the preparation stage of a verification flow. This command does not operate
        on partly selected designs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module (default='top')


    .. code:: yoscrypt

        -auto-top

    ::

            automatically determine the top of the design hierarchy


    .. code:: yoscrypt

        -flatten

    ::

            flatten the design before synthesis. this will pass '-auto-top' to
            'hierarchy' if no top module is specified.


    .. code:: yoscrypt

        -ifx

    ::

            passed to 'proc'. uses verilog simulation behavior for verilog if/case
            undef handling. this also prevents 'wreduce' from being run.


    .. code:: yoscrypt

        -memx

    ::

            simulate verilog simulation behavior for out-of-bounds memory accesses
            using the 'memory_memx' pass.


    .. code:: yoscrypt

        -nomem

    ::

            do not run any of the memory_* passes


    .. code:: yoscrypt

        -rdff

    ::

            call 'memory_dff'. This enables merging of FFs into
            memory read ports.


    .. code:: yoscrypt

        -nokeepdc

    ::

            do not call opt_* with -keepdc


    .. code:: yoscrypt

        -run <from_label>[:<to_label>]

    ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.



    ::

        The following commands are executed by this synthesis command:

            begin:
                hierarchy -check [-top <top> | -auto-top]

            coarse:
                proc [-ifx]
                flatten    (if -flatten)
                future
                opt_expr -keepdc
                opt_clean
                check
                opt -noff -keepdc
                wreduce -keepdc [-memx]
                memory_dff    (if -rdff)
                memory_memx    (if -memx)
                opt_clean
                memory_collect
                opt -noff -keepdc -fast

            check:
                stat
                check

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            prep [options]
        
        This command runs a conservative RTL synthesis. A typical application for this
        is the preparation stage of a verification flow. This command does not operate
        on partly selected designs.
        
            -top <module>
                use the specified module as top module (default='top')
        
            -auto-top
                automatically determine the top of the design hierarchy
        
            -flatten
                flatten the design before synthesis. this will pass '-auto-top' to
                'hierarchy' if no top module is specified.
        
            -ifx
                passed to 'proc'. uses verilog simulation behavior for verilog if/case
                undef handling. this also prevents 'wreduce' from being run.
        
            -memx
                simulate verilog simulation behavior for out-of-bounds memory accesses
                using the 'memory_memx' pass.
        
            -nomem
                do not run any of the memory_* passes
        
            -rdff
                call 'memory_dff'. This enables merging of FFs into
                memory read ports.
        
            -nokeepdc
                do not call opt_* with -keepdc
        
            -run <from_label>[:<to_label>]
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                hierarchy -check [-top <top> | -auto-top]
        
            coarse:
                proc [-ifx]
                flatten    (if -flatten)
                future
                opt_expr -keepdc
                opt_clean
                check
                opt -noff -keepdc
                wreduce -keepdc [-memx]
                memory_dff    (if -rdff)
                memory_memx    (if -memx)
                opt_clean
                memory_collect
                opt -noff -keepdc -fast
        
            check:
                stat
                check
        
