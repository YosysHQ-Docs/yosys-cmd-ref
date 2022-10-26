=======================================
opt_merge - consolidate identical cells
=======================================

.. only:: html

    :code:`yosys> help opt_merge`
    ----------------------------------------------------------------------------


    :code:`opt_merge [options] [selection]` ::

        This pass identifies cells with identical type and input signals. Such cells
        are then merged to one cell.


    :code:`-nomux` ::

            Do not merge MUX cells.


    :code:`-share_all` ::

            Operate on all cell types, not just built-in types.


    :code:`-keepdc` ::

            Do not merge flipflops with don't-care bits in their initial value.

.. only:: latex

    ::

        
            opt_merge [options] [selection]
        
        This pass identifies cells with identical type and input signals. Such cells
        are then merged to one cell.
        
            -nomux
                Do not merge MUX cells.
        
            -share_all
                Operate on all cell types, not just built-in types.
        
            -keepdc
                Do not merge flipflops with don't-care bits in their initial value.
        
