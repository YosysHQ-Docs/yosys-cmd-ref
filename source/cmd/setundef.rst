======================================================
setundef - replace undef values with defined constants
======================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: setundef
    :title: replace undef values with defined constants



    .. code:: yoscrypt

        setundef [options] [selection]

    ::

        This command replaces undef (x) constants with defined (0/1) constants.


    .. code:: yoscrypt

        -undriven

    ::

            also set undriven nets to constant values


    .. code:: yoscrypt

        -expose

    ::

            also expose undriven nets as inputs (use with -undriven)


    .. code:: yoscrypt

        -zero

    ::

            replace with bits cleared (0)


    .. code:: yoscrypt

        -one

    ::

            replace with bits set (1)


    .. code:: yoscrypt

        -undef

    ::

            replace with undef (x) bits, may be used with -undriven


    .. code:: yoscrypt

        -anyseq

    ::

            replace with $anyseq drivers (for formal)


    .. code:: yoscrypt

        -anyconst

    ::

            replace with $anyconst drivers (for formal)


    .. code:: yoscrypt

        -random <seed>

    ::

            replace with random bits using the specified integer as seed
            value for the random number generator.


    .. code:: yoscrypt

        -init

    ::

            also create/update init values for flip-flops


    .. code:: yoscrypt

        -params

    ::

            replace undef in cell parameters

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            setundef [options] [selection]
        
        This command replaces undef (x) constants with defined (0/1) constants.
        
            -undriven
                also set undriven nets to constant values
        
            -expose
                also expose undriven nets as inputs (use with -undriven)
        
            -zero
                replace with bits cleared (0)
        
            -one
                replace with bits set (1)
        
            -undef
                replace with undef (x) bits, may be used with -undriven
        
            -anyseq
                replace with $anyseq drivers (for formal)
        
            -anyconst
                replace with $anyconst drivers (for formal)
        
            -random <seed>
                replace with random bits using the specified integer as seed
                value for the random number generator.
        
            -init
                also create/update init values for flip-flops
        
            -params
                replace undef in cell parameters
        
