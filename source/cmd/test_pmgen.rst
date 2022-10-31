================================
test_pmgen - test pass for pmgen
================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help test_pmgen`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        test_pmgen -reduce_chain [options] [selection]

    ::

        Demo for recursive pmgen patterns. Map chains of AND/OR/XOR to $reduce_*.


    .. code:: yoscrypt

        test_pmgen -reduce_tree [options] [selection]

    ::

        Demo for recursive pmgen patterns. Map trees of AND/OR/XOR to $reduce_*.


    .. code:: yoscrypt

        test_pmgen -eqpmux [options] [selection]

    ::

        Demo for recursive pmgen patterns. Optimize EQ/NE/PMUX circuits.


    .. code:: yoscrypt

        test_pmgen -generate [options] <pattern_name>

    ::

        Create modules that match the specified pattern.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            test_pmgen -reduce_chain [options] [selection]
        
        Demo for recursive pmgen patterns. Map chains of AND/OR/XOR to $reduce_*.
        
        
            test_pmgen -reduce_tree [options] [selection]
        
        Demo for recursive pmgen patterns. Map trees of AND/OR/XOR to $reduce_*.
        
        
            test_pmgen -eqpmux [options] [selection]
        
        Demo for recursive pmgen patterns. Optimize EQ/NE/PMUX circuits.
        
        
            test_pmgen -generate [options] <pattern_name>
        
        Create modules that match the specified pattern.
        
