==================================================
chformal - change formal constraints of the design
==================================================

.. only:: html

    :code:`yosys> help chformal`
    ----------------------------------------------------------------------------


    :code:`chformal [types] [mode] [options] [selection]` ::

        Make changes to the formal constraints of the design. The [types] options
        the type of constraint to operate on. If none of the following options are
        given, the command will operate on all constraint types:


    :code:`-assert       $assert cells, representing assert(...) constraints`

    :code:`-assume       $assume cells, representing assume(...) constraints`

    :code:`-live         $live cells, representing assert(s_eventually ...)`

    :code:`-fair         $fair cells, representing assume(s_eventually ...)`

    :code:`-cover        $cover cells, representing cover() statements`

    ::

        Exactly one of the following modes must be specified:

    :code:`-remove` ::

            remove the cells and thus constraints from the design


    :code:`-early` ::

            bypass FFs that only delay the activation of a constraint


    :code:`-delay <N>` ::

            delay activation of the constraint by <N> clock cycles


    :code:`-skip <N>` ::

            ignore activation of the constraint in the first <N> clock cycles


    :code:`-assert2assume`

    :code:`-assume2assert`

    :code:`-live2fair`

    :code:`-fair2live` ::

            change the roles of cells as indicated. these options can be combined

.. only:: latex

    ::

        
            chformal [types] [mode] [options] [selection]
        
        Make changes to the formal constraints of the design. The [types] options
        the type of constraint to operate on. If none of the following options are
        given, the command will operate on all constraint types:
        
            -assert       $assert cells, representing assert(...) constraints
            -assume       $assume cells, representing assume(...) constraints
            -live         $live cells, representing assert(s_eventually ...)
            -fair         $fair cells, representing assume(s_eventually ...)
            -cover        $cover cells, representing cover() statements
        
        Exactly one of the following modes must be specified:
        
            -remove
                remove the cells and thus constraints from the design
        
            -early
                bypass FFs that only delay the activation of a constraint
        
            -delay <N>
                delay activation of the constraint by <N> clock cycles
        
            -skip <N>
                ignore activation of the constraint in the first <N> clock cycles
        
            -assert2assume
            -assume2assert
            -live2fair
            -fair2live
                change the roles of cells as indicated. these options can be combined
        
