=====================================================================
extractinv - extract explicit inverter cells for invertible cell pins
=====================================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help extractinv`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        extractinv [options] [selection]

    ::

        Searches the design for all cells with invertible pins controlled by a cell
        parameter (eg. IS_CLK_INVERTED on many Xilinx cells) and removes the parameter.
        If the parameter was set to 1, inserts an explicit inverter cell in front of
        the pin instead.  Normally used for output to ISE, which does not support the
        inversion parameters.

        To mark a cell port as invertible, use (* invertible_pin = "param_name" *)
        on the wire in the blackbox module.  The parameter value should have
        the same width as the port, and will be effectively XORed with it.


    .. code:: yoscrypt

        -inv <celltype> <portname_out>:<portname_in>

    ::

            Specifies the cell type to use for the inverters and its port names.
            This option is required.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            extractinv [options] [selection]
        
        Searches the design for all cells with invertible pins controlled by a cell
        parameter (eg. IS_CLK_INVERTED on many Xilinx cells) and removes the parameter.
        If the parameter was set to 1, inserts an explicit inverter cell in front of
        the pin instead.  Normally used for output to ISE, which does not support the
        inversion parameters.
        
        To mark a cell port as invertible, use (* invertible_pin = "param_name" *)
        on the wire in the blackbox module.  The parameter value should have
        the same width as the port, and will be effectively XORed with it.
        
            -inv <celltype> <portname_out>:<portname_in>
                Specifies the cell type to use for the inverters and its port names.
                This option is required.
        
