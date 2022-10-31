============================================================
dffunmap - unmap clock enable and synchronous reset from FFs
============================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help dffunmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        dffunmap [options] [selection]

    ::

        This pass transforms FF types with clock enable and/or synchronous reset into
        their base type (with neither clock enable nor sync reset) by emulating the
        clock enable and synchronous reset with multiplexers on the cell input.


    .. code:: yoscrypt

        -ce-only

    ::

            unmap only clock enables, leave synchronous resets alone.


    .. code:: yoscrypt

        -srst-only

    ::

            unmap only synchronous resets, leave clock enables alone.

.. raw:: latex

    \end{comment}

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
        
