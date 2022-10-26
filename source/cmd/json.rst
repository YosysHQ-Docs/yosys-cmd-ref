==================================
json - write design in JSON format
==================================

.. only:: html

    :code:`yosys> help json`
    ----------------------------------------------------------------------------


    :code:`json [options] [selection]` ::

        Write a JSON netlist of all selected objects.


    :code:`-o <filename>` ::

            write to the specified file.


    :code:`-aig` ::

            also include AIG models for the different gate types


    :code:`-compat-int` ::

            emit 32-bit or smaller fully-defined parameter values directly
            as JSON numbers (for compatibility with old parsers)


    ::

        See 'help write_json' for a description of the JSON format used.

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
        
