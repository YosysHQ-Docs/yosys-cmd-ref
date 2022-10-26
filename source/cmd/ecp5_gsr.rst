===========================
ecp5_gsr - ECP5: handle GSR
===========================

.. only:: html

    :code:`yosys> help ecp5_gsr`
    ----------------------------------------------------------------------------


    :code:`ecp5_gsr [options] [selection]` ::

        Trim active low async resets connected to GSR and resolve GSR parameter,
        if a GSR or SGSR primitive is used in the design.

        If any cell has the GSR parameter set to "AUTO", this will be resolved
        to "ENABLED" if a GSR primitive is present and the (* nogsr *) attribute
        is not set, otherwise it will be resolved to "DISABLED".

.. only:: latex

    ::

        
            ecp5_gsr [options] [selection]
        
        Trim active low async resets connected to GSR and resolve GSR parameter,
        if a GSR or SGSR primitive is used in the design.
        
        If any cell has the GSR parameter set to "AUTO", this will be resolved
        to "ENABLED" if a GSR primitive is present and the (* nogsr *) attribute
        is not set, otherwise it will be resolved to "DISABLED".
        
