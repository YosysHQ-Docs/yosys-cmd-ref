==================================
json - write design in JSON format
==================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help json`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        json [options] [selection]

    ::

        Write a JSON netlist of all selected objects.


    .. code:: yoscrypt

        -o <filename>

    ::

            write to the specified file.


    .. code:: yoscrypt

        -aig

    ::

            also include AIG models for the different gate types


    .. code:: yoscrypt

        -compat-int

    ::

            emit 32-bit or smaller fully-defined parameter values directly
            as JSON numbers (for compatibility with old parsers)


    ::

        See 'help write_json' for a description of the JSON format used.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            json [options] [selection]
        
        Write a JSON netlist of all selected objects.
        
            -o <filename>
                write to the specified file.
        
            -aig
                also include AIG models for the different gate types
        
            -compat-int
                emit 32-bit or smaller fully-defined parameter values directly
                as JSON numbers (for compatibility with old parsers)
        
        See 'help write_json' for a description of the JSON format used.
        
