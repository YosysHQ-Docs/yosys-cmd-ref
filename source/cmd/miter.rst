============================================
miter - automatically create a miter circuit
============================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help miter`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        miter -equiv [options] gold_name gate_name miter_name

    ::

        Creates a miter circuit for equivalence checking. The gold- and gate- modules
        must have the same interfaces. The miter circuit will have all inputs of the
        two source modules, prefixed with 'in_'. The miter circuit has a 'trigger'
        output that goes high if an output mismatch between the two source modules is
        detected.


    .. code:: yoscrypt

        -ignore_gold_x

    ::

            a undef (x) bit in the gold module output will match any value in
            the gate module output.


    .. code:: yoscrypt

        -make_outputs

    ::

            also route the gold- and gate-outputs to 'gold_*' and 'gate_*' outputs
            on the miter circuit.


    .. code:: yoscrypt

        -make_outcmp

    ::

            also create a cmp_* output for each gold/gate output pair.


    .. code:: yoscrypt

        -make_assert

    ::

            also create an 'assert' cell that checks if trigger is always low.


    .. code:: yoscrypt

        -flatten

    ::

            call 'flatten -wb; opt_expr -keepdc -undriven;;' on the miter circuit.


    .. code:: yoscrypt

        miter -assert [options] module [miter_name]

    ::

        Creates a miter circuit for property checking. All input ports are kept,
        output ports are discarded. An additional output 'trigger' is created that
        goes high when an assert is violated. Without a miter_name, the existing
        module is modified.


    .. code:: yoscrypt

        -make_outputs

    ::

            keep module output ports.


    .. code:: yoscrypt

        -flatten

    ::

            call 'flatten -wb; opt_expr -keepdc -undriven;;' on the miter circuit.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            miter -equiv [options] gold_name gate_name miter_name
        
        Creates a miter circuit for equivalence checking. The gold- and gate- modules
        must have the same interfaces. The miter circuit will have all inputs of the
        two source modules, prefixed with 'in_'. The miter circuit has a 'trigger'
        output that goes high if an output mismatch between the two source modules is
        detected.
        
            -ignore_gold_x
                a undef (x) bit in the gold module output will match any value in
                the gate module output.
        
            -make_outputs
                also route the gold- and gate-outputs to 'gold_*' and 'gate_*' outputs
                on the miter circuit.
        
            -make_outcmp
                also create a cmp_* output for each gold/gate output pair.
        
            -make_assert
                also create an 'assert' cell that checks if trigger is always low.
        
            -flatten
                call 'flatten -wb; opt_expr -keepdc -undriven;;' on the miter circuit.
        
        
            miter -assert [options] module [miter_name]
        
        Creates a miter circuit for property checking. All input ports are kept,
        output ports are discarded. An additional output 'trigger' is created that
        goes high when an assert is violated. Without a miter_name, the existing
        module is modified.
        
            -make_outputs
                keep module output ports.
        
            -flatten
                call 'flatten -wb; opt_expr -keepdc -undriven;;' on the miter circuit.
        
