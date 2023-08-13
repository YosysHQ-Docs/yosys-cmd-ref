===========================
ecp5_gsr - ECP5: handle GSR
===========================

.. raw:: latex

    \begin{comment}

.. cmd:def:: ecp5_gsr
    :title: ECP5: handle GSR



    .. code:: yoscrypt

        ecp5_gsr [options] [selection]

    ::

        Trim active low async resets connected to GSR and resolve GSR parameter,
        if a GSR or SGSR primitive is used in the design.

        If any cell has the GSR parameter set to "AUTO", this will be resolved
        to "ENABLED" if a GSR primitive is present and the (* nogsr *) attribute
        is not set, otherwise it will be resolved to "DISABLED".

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            ecp5_gsr [options] [selection]
        
        Trim active low async resets connected to GSR and resolve GSR parameter,
        if a GSR or SGSR primitive is used in the design.
        
        If any cell has the GSR parameter set to "AUTO", this will be resolved
        to "ENABLED" if a GSR primitive is present and the (* nogsr *) attribute
        is not set, otherwise it will be resolved to "DISABLED".
        
