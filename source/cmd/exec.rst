=====================================================
exec - execute commands in the operating system shell
=====================================================

.. only:: html

    :code:`yosys> help exec`
    ----------------------------------------------------------------------------


    :code:`exec [options] -- [command]` ::

        Execute a command in the operating system shell.  All supplied arguments are
        concatenated and passed as a command to popen(3).  Whitespace is not guaranteed
        to be preserved, even if quoted.  stdin and stderr are not connected, while
        stdout is logged unless the "-q" option is specified.



    :code:`-q` ::

            Suppress stdout and stderr from subprocess


    :code:`-expect-return <int>` ::

            Generate an error if popen() does not return specified value.
            May only be specified once; the final specified value is controlling
            if specified multiple times.


    :code:`-expect-stdout <regex>` ::

            Generate an error if the specified regex does not match any line
            in subprocess's stdout.  May be specified multiple times.


    :code:`-not-expect-stdout <regex>` ::

            Generate an error if the specified regex matches any line
            in subprocess's stdout.  May be specified multiple times.



    ::

        Example: exec -q -expect-return 0 -- echo "bananapie" | grep "nana"


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
        
        
