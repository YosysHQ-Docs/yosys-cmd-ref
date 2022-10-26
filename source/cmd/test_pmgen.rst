================================
test_pmgen - test pass for pmgen
================================

.. only:: html

    :code:`yosys> help test_pmgen`
    ----------------------------------------------------------------------------


    :code:`test_pmgen -reduce_chain [options] [selection]` ::

        Demo for recursive pmgen patterns. Map chains of AND/OR/XOR to $reduce_*.



    :code:`test_pmgen -reduce_tree [options] [selection]` ::

        Demo for recursive pmgen patterns. Map trees of AND/OR/XOR to $reduce_*.



    :code:`test_pmgen -eqpmux [options] [selection]` ::

        Demo for recursive pmgen patterns. Optimize EQ/NE/PMUX circuits.



    :code:`test_pmgen -generate [options] <pattern_name>` ::

        Create modules that match the specified pattern.

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
        
