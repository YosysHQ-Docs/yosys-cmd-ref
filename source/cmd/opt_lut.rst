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


    .. code:: yoscrypt

        -dlogic <type>:<cell-port>=<LUT-input>[:<cell-port>=<LUT-input>...]

    ::

            preserve connections to dedicated logic cell <type> that has ports
            <cell-port> connected to LUT inputs <LUT-input>. this includes
            the case where both LUT and dedicated logic input are connected to
            the same constant.


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
        
            -dlogic <type>:<cell-port>=<LUT-input>[:<cell-port>=<LUT-input>...]
                preserve connections to dedicated logic cell <type> that has ports
                <cell-port> connected to LUT inputs <LUT-input>. this includes
                the case where both LUT and dedicated logic input are connected to
                the same constant.
        
            -limit N
                only perform the first N combines, then stop. useful for debugging.
        
