========================================================
scc - detect strongly connected components (logic loops)
========================================================

.. only:: html

    :code:`yosys> help scc`
    ----------------------------------------------------------------------------


    :code:`scc [options] [selection]` ::

        This command identifies strongly connected components (aka logic loops) in the
        design.


    :code:`-expect <num>` ::

            expect to find exactly <num> SCCs. A different number of SCCs will
            produce an error.


    :code:`-max_depth <num>` ::

            limit to loops not longer than the specified number of cells. This
            can e.g. be useful in identifying small local loops in a module that
            implements one large SCC.


    :code:`-nofeedback` ::

            do not count cells that have their output fed back into one of their
            inputs as single-cell scc.


    :code:`-all_cell_types` ::

            Usually this command only considers internal non-memory cells. With
            this option set, all cells are considered. For unknown cells all ports
            are assumed to be bidirectional 'inout' ports.


    :code:`-set_attr <name> <value>` ::

            set the specified attribute on all cells that are part of a logic
            loop. the special token {} in the value is replaced with a unique
            identifier for the logic loop.


    :code:`-select` ::

            replace the current selection with a selection of all cells and wires
            that are part of a found logic loop


    :code:`-specify` ::

            examine specify rules to detect logic loops in whitebox/blackbox cells

.. only:: latex

    ::

        
            scc [options] [selection]
        
        This command identifies strongly connected components (aka logic loops) in the
        design.
        
            -expect <num>
                expect to find exactly <num> SCCs. A different number of SCCs will
                produce an error.
        
            -max_depth <num>
                limit to loops not longer than the specified number of cells. This
                can e.g. be useful in identifying small local loops in a module that
                implements one large SCC.
        
            -nofeedback
                do not count cells that have their output fed back into one of their
                inputs as single-cell scc.
        
            -all_cell_types
                Usually this command only considers internal non-memory cells. With
                this option set, all cells are considered. For unknown cells all ports
                are assumed to be bidirectional 'inout' ports.
        
            -set_attr <name> <value>
                set the specified attribute on all cells that are part of a logic
                loop. the special token {} in the value is replaced with a unique
                identifier for the logic loop.
        
            -select
                replace the current selection with a selection of all cells and wires
                that are part of a found logic loop
        
            -specify
                examine specify rules to detect logic loops in whitebox/blackbox cells
        
