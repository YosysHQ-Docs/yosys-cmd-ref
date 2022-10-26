============================
opt_lut - optimize LUT cells
============================

.. only:: html

    :code:`yosys> help opt_lut`
    ----------------------------------------------------------------------------


    :code:`opt_lut [options] [selection]` ::

        This pass combines cascaded $lut cells with unused inputs.


    :code:`-dlogic <type>:<cell-port>=<LUT-input>[:<cell-port>=<LUT-input>...]` ::

            preserve connections to dedicated logic cell <type> that has ports
            <cell-port> connected to LUT inputs <LUT-input>. this includes
            the case where both LUT and dedicated logic input are connected to
            the same constant.


    :code:`-limit N` ::

            only perform the first N combines, then stop. useful for debugging.

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
        
