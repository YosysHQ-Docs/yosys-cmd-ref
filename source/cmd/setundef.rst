======================================================
setundef - replace undef values with defined constants
======================================================

.. only:: html

    :code:`yosys> help setundef`
    ----------------------------------------------------------------------------


    :code:`setundef [options] [selection]` ::

        This command replaces undef (x) constants with defined (0/1) constants.


    :code:`-undriven` ::

            also set undriven nets to constant values


    :code:`-expose` ::

            also expose undriven nets as inputs (use with -undriven)


    :code:`-zero` ::

            replace with bits cleared (0)


    :code:`-one` ::

            replace with bits set (1)


    :code:`-undef` ::

            replace with undef (x) bits, may be used with -undriven


    :code:`-anyseq` ::

            replace with $anyseq drivers (for formal)


    :code:`-anyconst` ::

            replace with $anyconst drivers (for formal)


    :code:`-random <seed>` ::

            replace with random bits using the specified integer as seed
            value for the random number generator.


    :code:`-init` ::

            also create/update init values for flip-flops


    :code:`-params` ::

            replace undef in cell parameters

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
        
