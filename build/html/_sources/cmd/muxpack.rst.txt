======================================
muxpack - $mux/$pmux cascades to $pmux
======================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help muxpack`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        muxpack [selection]

    ::

        This pass converts cascaded chains of $pmux cells (e.g. those create from case
        constructs) and $mux cells (e.g. those created by if-else constructs) into
        $pmux cells.

        This optimisation is conservative --- it will only pack $mux or $pmux cells
        whose select lines are driven by '$eq' cells with other such cells if it can be
        certain that their select inputs are mutually exclusive.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            muxpack [selection]
        
        This pass converts cascaded chains of $pmux cells (e.g. those create from case
        constructs) and $mux cells (e.g. those created by if-else constructs) into
        $pmux cells.
        
        This optimisation is conservative --- it will only pack $mux or $pmux cells
        whose select lines are driven by '$eq' cells with other such cells if it can be
        certain that their select inputs are mutually exclusive.
        
