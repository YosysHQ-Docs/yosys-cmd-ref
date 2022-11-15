=====================================
tee - redirect command output to file
=====================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help tee`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        tee [-q] [-o logfile|-a logfile] cmd

    ::

        Execute the specified command, optionally writing the commands output to the
        specified logfile(s).


    .. code:: yoscrypt

        -q

    ::

            Do not print output to the normal destination (console and/or log file).


    .. code:: yoscrypt

        -o logfile

    ::

            Write output to this file, truncate if exists.


    .. code:: yoscrypt

        -a logfile

    ::

            Write output to this file, append if exists.


    ::

        +INT, -INT
            Add/subtract INT from the -v setting for this command.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            tee [-q] [-o logfile|-a logfile] cmd
        
        Execute the specified command, optionally writing the commands output to the
        specified logfile(s).
        
            -q
                Do not print output to the normal destination (console and/or log file).
        
            -o logfile
                Write output to this file, truncate if exists.
        
            -a logfile
                Write output to this file, append if exists.
        
            +INT, -INT
                Add/subtract INT from the -v setting for this command.
        
