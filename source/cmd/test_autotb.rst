==========================================
test_autotb - generate simple test benches
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: test_autotb
    :title: generate simple test benches



    .. code:: yoscrypt

        test_autotb [options] [filename]

    ::

        Automatically create primitive Verilog test benches for all modules in the
        design. The generated testbenches toggle the input pins of the module in
        a semi-random manner and dumps the resulting output signals.

        This can be used to check the synthesis results for simple circuits by
        comparing the testbench output for the input files and the synthesis results.

        The backend automatically detects clock signals. Additionally a signal can
        be forced to be interpreted as clock signal by setting the attribute
        'gentb_clock' on the signal.

        The attribute 'gentb_constant' can be used to force a signal to a constant
        value after initialization. This can e.g. be used to force a reset signal
        low in order to explore more inner states in a state machine.

        The attribute 'gentb_skip' can be attached to modules to suppress testbench
        generation.


    .. code:: yoscrypt

        -n <int>

    ::

            number of iterations the test bench should run (default = 1000)


    .. code:: yoscrypt

        -seed <int>

    ::

            seed used for pseudo-random number generation (default = 0).
            a value of 0 will cause an arbitrary seed to be chosen, based on
            the current system time.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            test_autotb [options] [filename]
        
        Automatically create primitive Verilog test benches for all modules in the
        design. The generated testbenches toggle the input pins of the module in
        a semi-random manner and dumps the resulting output signals.
        
        This can be used to check the synthesis results for simple circuits by
        comparing the testbench output for the input files and the synthesis results.
        
        The backend automatically detects clock signals. Additionally a signal can
        be forced to be interpreted as clock signal by setting the attribute
        'gentb_clock' on the signal.
        
        The attribute 'gentb_constant' can be used to force a signal to a constant
        value after initialization. This can e.g. be used to force a reset signal
        low in order to explore more inner states in a state machine.
        
        The attribute 'gentb_skip' can be attached to modules to suppress testbench
        generation.
        
            -n <int>
                number of iterations the test bench should run (default = 1000)
        
            -seed <int>
                seed used for pseudo-random number generation (default = 0).
                a value of 0 will cause an arbitrary seed to be chosen, based on
                the current system time.
        
