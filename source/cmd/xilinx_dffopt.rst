========================================================
xilinx_dffopt - Xilinx: optimize FF control signal usage
========================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help xilinx_dffopt`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        xilinx_dffopt [options] [selection]

    ::

        Converts hardware clock enable and set/reset signals on FFs to emulation
        using LUTs, if doing so would improve area.  Operates on post-techmap Xilinx
        cells (LUT*, FD*).


    .. code:: yoscrypt

        -lut4

    ::

            Assume a LUT4-based device (instead of a LUT6-based device).

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            xilinx_dffopt [options] [selection]
        
        Converts hardware clock enable and set/reset signals on FFs to emulation
        using LUTs, if doing so would improve area.  Operates on post-techmap Xilinx
        cells (LUT*, FD*).
        
            -lut4
                Assume a LUT4-based device (instead of a LUT6-based device).
        
