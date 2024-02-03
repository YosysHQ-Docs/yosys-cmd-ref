==================================================
chformal - change formal constraints of the design
==================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help chformal`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        chformal [types] [mode] [options] [selection]

    ::

        Make changes to the formal constraints of the design. The [types] options
        the type of constraint to operate on. If none of the following options are
        given, the command will operate on all constraint types:


    .. code:: yoscrypt

        -assert       $assert cells, representing assert(...) constraints

   

    .. code:: yoscrypt

        -assume       $assume cells, representing assume(...) constraints

   

    .. code:: yoscrypt

        -live         $live cells, representing assert(s_eventually ...)

   

    .. code:: yoscrypt

        -fair         $fair cells, representing assume(s_eventually ...)

   

    .. code:: yoscrypt

        -cover        $cover cells, representing cover() statements

   

    ::

        Additionally chformal will operate on $check cells corresponding to the

    ::

        selected constraint types.

    ::

        Exactly one of the following modes must be specified:

    .. code:: yoscrypt

        -remove

    ::

            remove the cells and thus constraints from the design


    .. code:: yoscrypt

        -early

    ::

            bypass FFs that only delay the activation of a constraint. When inputs
            of the bypassed FFs do not remain stable between clock edges, this may
            result in unexpected behavior.


    .. code:: yoscrypt

        -delay <N>

    ::

            delay activation of the constraint by <N> clock cycles


    .. code:: yoscrypt

        -skip <N>

    ::

            ignore activation of the constraint in the first <N> clock cycles


    .. code:: yoscrypt

        -coverenable

    ::

            add cover statements for the enable signals of the constraints

            Note: For the Verific frontend it is currently not guaranteed that a
            reachable SVA statement corresponds to an active enable signal.


    .. code:: yoscrypt

        -assert2assume

   

    .. code:: yoscrypt

        -assume2assert

   

    .. code:: yoscrypt

        -live2fair

   

    .. code:: yoscrypt

        -fair2live

    ::

            change the roles of cells as indicated. these options can be combined


    .. code:: yoscrypt

        -lower

    ::

            convert each $check cell into an $assert, $assume, $live, $fair or
            $cover cell. If the $check cell contains a message, also produce a
            $print cell.

.. raw:: latex

    \end{comment}

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
        
            Additionally chformal will operate on $check cells corresponding to the
            selected constraint types.
        
        Exactly one of the following modes must be specified:
        
            -remove
                remove the cells and thus constraints from the design
        
            -early
                bypass FFs that only delay the activation of a constraint. When inputs
                of the bypassed FFs do not remain stable between clock edges, this may
                result in unexpected behavior.
        
            -delay <N>
                delay activation of the constraint by <N> clock cycles
        
            -skip <N>
                ignore activation of the constraint in the first <N> clock cycles
        
            -coverenable
                add cover statements for the enable signals of the constraints
        
                Note: For the Verific frontend it is currently not guaranteed that a
                reachable SVA statement corresponds to an active enable signal.
        
            -assert2assume
            -assume2assert
            -live2fair
            -fair2live
                change the roles of cells as indicated. these options can be combined
        
            -lower
                convert each $check cell into an $assert, $assume, $live, $fair or
                $cover cell. If the $check cell contains a message, also produce a
                $print cell.
        
