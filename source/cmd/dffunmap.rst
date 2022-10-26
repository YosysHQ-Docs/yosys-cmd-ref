============================================================
dffunmap - unmap clock enable and synchronous reset from FFs
============================================================

.. only:: html

    :code:`yosys> help dffunmap`
    ----------------------------------------------------------------------------


    :code:`dffunmap [options] [selection]` ::

        This pass transforms FF types with clock enable and/or synchronous reset into
        their base type (with neither clock enable nor sync reset) by emulating the
        clock enable and synchronous reset with multiplexers on the cell input.


    :code:`-ce-only` ::

            unmap only clock enables, leave synchronous resets alone.


    :code:`-srst-only` ::

            unmap only synchronous resets, leave clock enables alone.

.. only:: latex

    ::

        
            dffunmap [options] [selection]
        
        This pass transforms FF types with clock enable and/or synchronous reset into
        their base type (with neither clock enable nor sync reset) by emulating the
        clock enable and synchronous reset with multiplexers on the cell input.
        
            -ce-only
                unmap only clock enables, leave synchronous resets alone.
        
            -srst-only
                unmap only synchronous resets, leave clock enables alone.
        
