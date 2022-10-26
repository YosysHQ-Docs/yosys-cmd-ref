====================================
ltp - print longest topological path
====================================

.. only:: html

    :code:`yosys> help ltp`
    ----------------------------------------------------------------------------


    :code:`ltp [options] [selection]` ::

        This command prints the longest topological path in the design. (Only considers
        paths within a single module, so the design must be flattened.)


    :code:`-noff` ::

            automatically exclude FF cell types

.. only:: latex

    ::

        
            ltp [options] [selection]
        
        This command prints the longest topological path in the design. (Only considers
        paths within a single module, so the design must be flattened.)
        
            -noff
                automatically exclude FF cell types
        
