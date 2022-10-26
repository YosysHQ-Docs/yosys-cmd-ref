=====================================
tee - redirect command output to file
=====================================

.. only:: html

    :code:`yosys> help tee`
    ----------------------------------------------------------------------------


    :code:`tee [-q] [-o logfile|-a logfile] cmd` ::

        Execute the specified command, optionally writing the commands output to the
        specified logfile(s).


    :code:`-q` ::

            Do not print output to the normal destination (console and/or log file).


    :code:`-o logfile` ::

            Write output to this file, truncate if exists.


    :code:`-a logfile` ::

            Write output to this file, append if exists.


    ::

        +INT, -INT
            Add/subtract INT from the -v setting for this command.

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
        
