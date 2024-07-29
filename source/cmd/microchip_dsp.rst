===================================================
microchip_dsp - MICROCHIP: pack resources into DSPs
===================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: microchip_dsp
    :title: MICROCHIP: pack resources into DSPs



    .. code:: yoscrypt

        microchip_dsp [options] [selection]

    ::

        Pack input registers 'A', 'B', 'C', and 'D' (with optional enable/reset),
        output register 'P' (with optional enable/reset), pre-adder and/or post-adder into
        Microchip DSP resources.

        Multiply-accumulate operations using the post-adder with feedback on the 'C'
        input will be folded into the DSP. In this scenario only, the 'C' input can be
        used to override the current accumulation result with a new value. This will
        be added to the multiplier result to form the next accumulation result.

        Use of the dedicated 'PCOUT' -> 'PCIN' cascade path is detected for 'P' -> 'C'
        connections (optionally, where 'P' is right-shifted by 17-bits and used as an
        input to the post-adder. This pattern is common for summing partial products to
        implement wide multipliers). Cascade chains are limited to a mazimum length 
        of 24 cells, corresponding to PolarFire (pf) devices.

        This pass is a no-op if the scratchpad variable 'microchip_dsp.multonly' is set
        to 1.



    .. code:: yoscrypt

        -family {polarfire}

    ::

            select the family to target
            default: polarfire

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            microchip_dsp [options] [selection]
        
        Pack input registers 'A', 'B', 'C', and 'D' (with optional enable/reset),
        output register 'P' (with optional enable/reset), pre-adder and/or post-adder into
        Microchip DSP resources.
        
        Multiply-accumulate operations using the post-adder with feedback on the 'C'
        input will be folded into the DSP. In this scenario only, the 'C' input can be
        used to override the current accumulation result with a new value. This will
        be added to the multiplier result to form the next accumulation result.
        
        Use of the dedicated 'PCOUT' -> 'PCIN' cascade path is detected for 'P' -> 'C'
        connections (optionally, where 'P' is right-shifted by 17-bits and used as an
        input to the post-adder. This pattern is common for summing partial products to
        implement wide multipliers). Cascade chains are limited to a mazimum length 
        of 24 cells, corresponding to PolarFire (pf) devices.
        
        This pass is a no-op if the scratchpad variable 'microchip_dsp.multonly' is set
        to 1.
        
        
            -family {polarfire}
                select the family to target
                default: polarfire
        
