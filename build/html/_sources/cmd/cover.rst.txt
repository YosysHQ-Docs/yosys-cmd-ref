====================================
cover - print code coverage counters
====================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help cover`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        cover [options] [pattern]

    ::

        Print the code coverage counters collected using the cover() macro in the Yosys
        C++ code. This is useful to figure out what parts of Yosys are utilized by a
        test bench.


    .. code:: yoscrypt

        -q

    ::

            Do not print output to the normal destination (console and/or log file)


    .. code:: yoscrypt

        -o file

    ::

            Write output to this file, truncate if exists.


    .. code:: yoscrypt

        -a file

    ::

            Write output to this file, append if exists.


    .. code:: yoscrypt

        -d dir

    ::

            Write output to a newly created file in the specified directory.


    ::

        When one or more pattern (shell wildcards) are specified, then only counters
        matching at least one pattern are printed.


        It is also possible to instruct Yosys to print the coverage counters on program
        exit to a file using environment variables:

            YOSYS_COVER_DIR="{dir-name}" yosys {args}

                This will create a file (with an auto-generated name) in this
                directory and write the coverage counters to it.

            YOSYS_COVER_FILE="{file-name}" yosys {args}

                This will append the coverage counters to the specified file.


        Hint: Use the following AWK command to consolidate Yosys coverage files:

            gawk '{ p[$3] = $1; c[$3] += $2; } END { for (i in p)
              printf "%-60s %10d %s\n", p[i], c[i], i; }' {files} | sort -k3


        Coverage counters are only available in Yosys for Linux.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            cover [options] [pattern]
        
        Print the code coverage counters collected using the cover() macro in the Yosys
        C++ code. This is useful to figure out what parts of Yosys are utilized by a
        test bench.
        
            -q
                Do not print output to the normal destination (console and/or log file)
        
            -o file
                Write output to this file, truncate if exists.
        
            -a file
                Write output to this file, append if exists.
        
            -d dir
                Write output to a newly created file in the specified directory.
        
        When one or more pattern (shell wildcards) are specified, then only counters
        matching at least one pattern are printed.
        
        
        It is also possible to instruct Yosys to print the coverage counters on program
        exit to a file using environment variables:
        
            YOSYS_COVER_DIR="{dir-name}" yosys {args}
        
                This will create a file (with an auto-generated name) in this
                directory and write the coverage counters to it.
        
            YOSYS_COVER_FILE="{file-name}" yosys {args}
        
                This will append the coverage counters to the specified file.
        
        
        Hint: Use the following AWK command to consolidate Yosys coverage files:
        
            gawk '{ p[$3] = $1; c[$3] += $2; } END { for (i in p)
              printf "%-60s %10d %s\n", p[i], c[i], i; }' {files} | sort -k3
        
        
        Coverage counters are only available in Yosys for Linux.
        
