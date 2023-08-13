=========================================
proc_prune - remove redundant assignments
=========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: proc_prune
    :title: remove redundant assignments



    .. code:: yoscrypt

        proc_prune [selection]

    ::

        This pass identifies assignments in processes that are always overwritten by
        a later assignment to the same signal and removes them.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            proc_prune [selection]
        
        This pass identifies assignments in processes that are always overwritten by
        a later assignment to the same signal and removes them.
        
