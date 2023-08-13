==========================================================
opt_mem_widen - optimize memories where all ports are wide
==========================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: opt_mem_widen
    :title: optimize memories where all ports are wide



    .. code:: yoscrypt

        opt_mem_widen [options] [selection]

    ::

        This pass looks for memories where all ports are wide and adjusts the base
        memory width up until that stops being the case.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            opt_mem_widen [options] [selection]
        
        This pass looks for memories where all ports are wide and adjusts the base
        memory width up until that stops being the case.
        
