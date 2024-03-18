=========================================================
gatemate_foldinv - fold inverters into Gatemate LUT trees
=========================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: gatemate_foldinv
    :title: fold inverters into Gatemate LUT trees



    .. code:: yoscrypt

        gatemate_foldinv [selection]

    ::

        This pass searches for $__CC_NOT cells and folds them into CC_LUT2, CC_L2T4
        and CC_L2T5 cells as created by LUT tree mapping.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            gatemate_foldinv [selection]
        
        
        This pass searches for $__CC_NOT cells and folds them into CC_LUT2, CC_L2T4
        and CC_L2T5 cells as created by LUT tree mapping.
        
