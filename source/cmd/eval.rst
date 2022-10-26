==========================================
eval - evaluate the circuit given an input
==========================================

.. only:: html

    :code:`yosys> help eval`
    ----------------------------------------------------------------------------


    :code:`eval [options] [selection]` ::

        This command evaluates the value of a signal given the value of all required
        inputs.


    :code:`-set <signal> <value>` ::

            set the specified signal to the specified value.


    :code:`-set-undef` ::

            set all unspecified source signals to undef (x)


    :code:`-table <signal>` ::

            create a truth table using the specified input signals


    :code:`-show <signal>` ::

            show the value for the specified signal. if no -show option is passed
            then all output ports of the current module are used.

.. only:: latex

    ::

        
            eval [options] [selection]
        
        This command evaluates the value of a signal given the value of all required
        inputs.
        
            -set <signal> <value>
                set the specified signal to the specified value.
        
            -set-undef
                set all unspecified source signals to undef (x)
        
            -table <signal>
                create a truth table using the specified input signals
        
            -show <signal>
                show the value for the specified signal. if no -show option is passed
                then all output ports of the current module are used.
        
