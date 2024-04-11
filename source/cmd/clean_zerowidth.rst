==============================================================
clean_zerowidth - clean zero-width connections from the design
==============================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: clean_zerowidth
    :title: clean zero-width connections from the design



    .. code:: yoscrypt

        clean_zerowidth [selection]

    ::

        Fixes the selected cells and processes to contain no zero-width connections.
        Depending on the cell type, this may be implemented by removing the connection,
        widening it to 1-bit, or removing the cell altogether.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            clean_zerowidth [selection]
        
        Fixes the selected cells and processes to contain no zero-width connections.
        Depending on the cell type, this may be implemented by removing the connection,
        widening it to 1-bit, or removing the cell altogether.
        
