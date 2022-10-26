==============================================================
clean_zerowidth - clean zero-width connections from the design
==============================================================

.. only:: html

    :code:`yosys> help clean_zerowidth`
    ----------------------------------------------------------------------------


    :code:`clean_zerowidth [selection]` ::

        Fixes the selected cells and processes to contain no zero-width connections.
        Depending on the cell type, this may be implemented by removing the connection,
        widening it to 1-bit, or removing the cell altogether.

.. only:: latex

    ::

        
            clean_zerowidth [selection]
        
        Fixes the selected cells and processes to contain no zero-width connections.
        Depending on the cell type, this may be implemented by removing the connection,
        widening it to 1-bit, or removing the cell altogether.
        
