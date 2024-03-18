=====================================================
exec - execute commands in the operating system shell
=====================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: exec
    :title: execute commands in the operating system shell



    .. code:: yoscrypt

        exec [options] -- [command]

    ::

        Execute a command in the operating system shell.  All supplied arguments are
        concatenated and passed as a command to popen(3).  Whitespace is not guaranteed
        to be preserved, even if quoted.  stdin and stderr are not connected, while
        stdout is logged unless the "-q" option is specified.



    .. code:: yoscrypt

        -q

    ::

            Suppress stdout and stderr from subprocess


    .. code:: yoscrypt

        -expect-return <int>

    ::

            Generate an error if popen() does not return specified value.
            May only be specified once; the final specified value is controlling
            if specified multiple times.


    .. code:: yoscrypt

        -expect-stdout <regex>

    ::

            Generate an error if the specified regex does not match any line
            in subprocess's stdout.  May be specified multiple times.


    .. code:: yoscrypt

        -not-expect-stdout <regex>

    ::

            Generate an error if the specified regex matches any line
            in subprocess's stdout.  May be specified multiple times.



    ::

        Example: exec -q -expect-return 0 -- echo "bananapie" | grep "nana"


.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            exec [options] -- [command]
        
        Execute a command in the operating system shell.  All supplied arguments are
        concatenated and passed as a command to popen(3).  Whitespace is not guaranteed
        to be preserved, even if quoted.  stdin and stderr are not connected, while
        stdout is logged unless the "-q" option is specified.
        
        
            -q
                Suppress stdout and stderr from subprocess
        
            -expect-return <int>
                Generate an error if popen() does not return specified value.
                May only be specified once; the final specified value is controlling
                if specified multiple times.
        
            -expect-stdout <regex>
                Generate an error if the specified regex does not match any line
                in subprocess's stdout.  May be specified multiple times.
        
            -not-expect-stdout <regex>
                Generate an error if the specified regex matches any line
                in subprocess's stdout.  May be specified multiple times.
        
        
            Example: exec -q -expect-return 0 -- echo "bananapie" | grep "nana"
        
        
