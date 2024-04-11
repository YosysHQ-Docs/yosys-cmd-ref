==========================================
eval - evaluate the circuit given an input
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: eval
    :title: evaluate the circuit given an input



    .. code:: yoscrypt

        eval [options] [selection]

    ::

        This command evaluates the value of a signal given the value of all required
        inputs.


    .. code:: yoscrypt

        -set <signal> <value>

    ::

            set the specified signal to the specified value.


    .. code:: yoscrypt

        -set-undef

    ::

            set all unspecified source signals to undef (x)


    .. code:: yoscrypt

        -table <signal>

    ::

            create a truth table using the specified input signals


    .. code:: yoscrypt

        -show <signal>

    ::

            show the value for the specified signal. if no -show option is passed
            then all output ports of the current module are used.

.. raw:: latex

    \end{comment}

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
        
