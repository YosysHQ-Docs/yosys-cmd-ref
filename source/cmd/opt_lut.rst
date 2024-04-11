============================
opt_lut - optimize LUT cells
============================

.. raw:: latex

    \begin{comment}

.. cmd:def:: opt_lut
    :title: optimize LUT cells



    .. code:: yoscrypt

        opt_lut [options] [selection]

    ::

        This pass combines cascaded $lut cells with unused inputs.

        	-tech ice40
                treat the design as a LUT-mapped circuit for the iCE40 architecture
                and preserve connections to SB_CARRY as appropriate


    .. code:: yoscrypt

        -limit N

    ::

            only perform the first N combines, then stop. useful for debugging.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            opt_lut [options] [selection]
        
        This pass combines cascaded $lut cells with unused inputs.
        
        	-tech ice40
                treat the design as a LUT-mapped circuit for the iCE40 architecture
                and preserve connections to SB_CARRY as appropriate
        
            -limit N
                only perform the first N combines, then stop. useful for debugging.
        
