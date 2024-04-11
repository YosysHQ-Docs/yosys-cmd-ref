============================================================
opt_demorgan - Optimize reductions with DeMorgan equivalents
============================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: opt_demorgan
    :title: Optimize reductions with DeMorgan equivalents



    .. code:: yoscrypt

        opt_demorgan [selection]

    ::

        This pass pushes inverters through $reduce_* cells if this will reduce the
        overall gate count of the circuit

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            opt_demorgan [selection]
        
        This pass pushes inverters through $reduce_* cells if this will reduce the
        overall gate count of the circuit
        
