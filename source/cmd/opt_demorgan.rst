============================================================
opt_demorgan - Optimize reductions with DeMorgan equivalents
============================================================

.. only:: html

    :code:`yosys> help opt_demorgan`
    ----------------------------------------------------------------------------


    :code:`opt_demorgan [selection]` ::

        This pass pushes inverters through $reduce_* cells if this will reduce the
        overall gate count of the circuit

.. only:: latex

    ::

        
            opt_demorgan [selection]
        
        This pass pushes inverters through $reduce_* cells if this will reduce the
        overall gate count of the circuit
        
