===========================================
booth - map $mul cells to Booth multipliers
===========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: booth
    :title: map $mul cells to Booth multipliers



    .. code:: yoscrypt

        booth [selection]

    ::

        This pass replaces multiplier cells with a radix-4 Booth-encoded implementation.
        It operates on $mul cells whose width of operands is at least 4x4 and whose
        width of result is at least 8.


    .. code:: yoscrypt

        -lowpower

    ::

            use an alternative low-power architecture for the generated multiplier
            (signed multipliers only)

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            booth [selection]
        
        This pass replaces multiplier cells with a radix-4 Booth-encoded implementation.
        It operates on $mul cells whose width of operands is at least 4x4 and whose
        width of result is at least 8.
        
            -lowpower
                use an alternative low-power architecture for the generated multiplier
                (signed multipliers only)
        
