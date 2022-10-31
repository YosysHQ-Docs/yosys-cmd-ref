================================================
write_table - write design as connectivity table
================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_table`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_table [options] [filename]

    ::

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
.. raw:: latex

    \end{comment}

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
