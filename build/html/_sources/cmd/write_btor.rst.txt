======================================
write_btor - write design to BTOR file
======================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_btor`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_btor [options] [filename]

    ::

        Write a BTOR description of the current design.


    .. code:: yoscrypt

        -v

    ::

          Add comments and indentation to BTOR output file


    .. code:: yoscrypt

        -s

    ::

          Output only a single bad property for all asserts


    .. code:: yoscrypt

        -c

    ::

          Output cover properties using 'bad' statements instead of asserts


    .. code:: yoscrypt

        -i <filename>

    ::

          Create additional info file with auxiliary information


    .. code:: yoscrypt

        -x

    ::

          Output symbols for internal netnames (starting with '$')

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_btor [options] [filename]
        
        Write a BTOR description of the current design.
        
          -v
            Add comments and indentation to BTOR output file
        
          -s
            Output only a single bad property for all asserts
        
          -c
            Output cover properties using 'bad' statements instead of asserts
        
          -i <filename>
            Create additional info file with auxiliary information
        
          -x
            Output symbols for internal netnames (starting with '$')
        
