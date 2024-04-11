=======================================
opt_merge - consolidate identical cells
=======================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: opt_merge
    :title: consolidate identical cells



    .. code:: yoscrypt

        opt_merge [options] [selection]

    ::

        This pass identifies cells with identical type and input signals. Such cells
        are then merged to one cell.


    .. code:: yoscrypt

        -nomux

    ::

            Do not merge MUX cells.


    .. code:: yoscrypt

        -share_all

    ::

            Operate on all cell types, not just built-in types.


    .. code:: yoscrypt

        -keepdc

    ::

            Do not merge flipflops with don't-care bits in their initial value.

.. raw:: latex

    \end{comment}

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
        
