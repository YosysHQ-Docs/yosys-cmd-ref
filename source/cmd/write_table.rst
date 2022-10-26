================================================
write_table - write design as connectivity table
================================================

.. only:: html

    :code:`yosys> help write_table`
    ----------------------------------------------------------------------------


    :code:`write_table [options] [filename]` ::

        Write the current design as connectivity table. The output is a tab-separated
        ASCII table with the following columns:

          module name
          cell name
          cell type
          cell port
          direction
          signal

        module inputs and outputs are output using cell type and port '-' and with
        'pi' (primary input) or 'po' (primary output) or 'pio' as direction.
.. only:: latex

    ::

        
            write_table [options] [filename]
        
        Write the current design as connectivity table. The output is a tab-separated
        ASCII table with the following columns:
        
          module name
          cell name
          cell type
          cell port
          direction
          signal
        
        module inputs and outputs are output using cell type and port '-' and with
        'pi' (primary input) or 'po' (primary output) or 'pio' as direction.
