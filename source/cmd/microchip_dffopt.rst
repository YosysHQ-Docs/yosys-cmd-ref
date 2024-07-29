==============================================================
microchip_dffopt - MICROCHIP: optimize FF control signal usage
==============================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: microchip_dffopt
    :title: MICROCHIP: optimize FF control signal usage



    .. code:: yoscrypt

        microchip_dffopt [options] [selection]

    ::

        Converts hardware clock enable and set/reset signals on FFs to emulation
        using LUTs, if doing so would improve area. Operates on post-techmap LUT, DFF
        cells. 

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            microchip_dffopt [options] [selection]
        
        Converts hardware clock enable and set/reset signals on FFs to emulation
        using LUTs, if doing so would improve area. Operates on post-techmap LUT, DFF
        cells. 
        
