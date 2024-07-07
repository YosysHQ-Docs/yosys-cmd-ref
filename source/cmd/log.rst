==============================
log - print text and log files
==============================

.. raw:: latex

    \begin{comment}

.. cmd:def:: log
    :title: print text and log files



    .. code:: yoscrypt

        log [options] string

   
    .. code:: yoscrypt

        log [ -push | -pop ]

    ::

        Print the given string to the screen and/or the log file. This is useful for TCL
        scripts, because the TCL command "puts" only goes to stdout but not to
        logfiles.


    .. code:: yoscrypt

        -stdout

    ::

            Print the output to stdout too. This is useful when all Yosys is
            executed with a script and the -q (quiet operation) argument to notify
            the user.


    .. code:: yoscrypt

        -stderr

    ::

            Print the output to stderr too.


    .. code:: yoscrypt

        -nolog

    ::

            Don't use the internal log() command. Use either -stdout or -stderr,
            otherwise no output will be generated at all.


    .. code:: yoscrypt

        -n

    ::

            do not append a newline


    .. code:: yoscrypt

        -header

    ::

            log a pass header


    .. code:: yoscrypt

        -push

    ::

            push a new level on the pass counter


    .. code:: yoscrypt

        -pop

    ::

            pop from the pass counter

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            log [options] string
            log [ -push | -pop ]
        
        Print the given string to the screen and/or the log file. This is useful for TCL
        scripts, because the TCL command "puts" only goes to stdout but not to
        logfiles.
        
            -stdout
                Print the output to stdout too. This is useful when all Yosys is
                executed with a script and the -q (quiet operation) argument to notify
                the user.
        
            -stderr
                Print the output to stderr too.
        
            -nolog
                Don't use the internal log() command. Use either -stdout or -stderr,
                otherwise no output will be generated at all.
        
            -n
                do not append a newline
        
            -header
                log a pass header
        
            -push
                push a new level on the pass counter
        
            -pop
                pop from the pass counter
        
