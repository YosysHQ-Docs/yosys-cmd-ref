============================
opt_lut - optimize LUT cells
============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help opt_lut`
--------------------------------------------------------------------------------

.. container:: cmdref


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


    ::

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
        
            -dlogic <type>:<cell-port>=<LUT-input>[:<cell-port>=<LUT-input>...]
                preserve connections to dedicated logic cell <type> that has ports
                <cell-port> connected to LUT inputs <LUT-input>. this includes
                the case where both LUT and dedicated logic input are connected to
                the same constant.
        
        	-tech ice40
                treat the design as a LUT-mapped circuit for the iCE40 architecture
                and preserve connections to SB_CARRY as appropriate
        
            -limit N
                only perform the first N combines, then stop. useful for debugging.
        
