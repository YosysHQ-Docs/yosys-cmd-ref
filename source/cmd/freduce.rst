======================================
freduce - perform functional reduction
======================================

.. only:: html

    :code:`yosys> help freduce`
    ----------------------------------------------------------------------------


    :code:`freduce [options] [selection]` ::

        This pass performs functional reduction in the circuit. I.e. if two nodes are
        equivalent, they are merged to one node and one of the redundant drivers is
        disconnected. A subsequent call to 'clean' will remove the redundant drivers.


    :code:`-v, -vv` ::

            enable verbose or very verbose output


    :code:`-inv` ::

            enable explicit handling of inverted signals


    :code:`-stop <n>` ::

            stop after <n> reduction operations. this is mostly used for
            debugging the freduce command itself.


    :code:`-dump <prefix>` ::

            dump the design to <prefix>_<module>_<num>.il after each reduction
            operation. this is mostly used for debugging the freduce command.


    ::

        This pass is undef-aware, i.e. it considers don't-care values for detecting
        equivalent nodes.

        All selected wires are considered for rewiring. The selected cells cover the
        circuit that is analyzed.

.. only:: latex

    ::

        
            freduce [options] [selection]
        
        This pass performs functional reduction in the circuit. I.e. if two nodes are
        equivalent, they are merged to one node and one of the redundant drivers is
        disconnected. A subsequent call to 'clean' will remove the redundant drivers.
        
            -v, -vv
                enable verbose or very verbose output
        
            -inv
                enable explicit handling of inverted signals
        
            -stop <n>
                stop after <n> reduction operations. this is mostly used for
                debugging the freduce command itself.
        
            -dump <prefix>
                dump the design to <prefix>_<module>_<num>.il after each reduction
                operation. this is mostly used for debugging the freduce command.
        
        This pass is undef-aware, i.e. it considers don't-care values for detecting
        equivalent nodes.
        
        All selected wires are considered for rewiring. The selected cells cover the
        circuit that is analyzed.
        
