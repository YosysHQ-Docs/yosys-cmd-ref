=========================================
proc_prune - remove redundant assignments
=========================================

.. only:: html

    :code:`yosys> help proc_prune`
    ----------------------------------------------------------------------------


    :code:`proc_prune [selection]` ::

        This pass identifies assignments in processes that are always overwritten by
        a later assignment to the same signal and removes them.

.. only:: latex

    ::

        
            proc_prune [selection]
        
        This pass identifies assignments in processes that are always overwritten by
        a later assignment to the same signal and removes them.
        
