===========================================
booth - map $mul cells to Booth multipliers
===========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help booth`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        booth [selection]

    ::

        This pass replaces multiplier cells with an implementation based on the Booth
        algorithm. It operates on $mul cells whose width of operands is at least 4x4
        and whose width of result is at least 8. The detailed architecture is selected
        from two options based on the signedness of the operands to the $mul cell.

        See the references below for the description of the architectures.

        Signed-multiplier architecture:
        Y. J. Chang, Y. C. Cheng, S. C. Liao and C. H. Hsiao, "A Low Power Radix-4 Booth
        Multiplier With Pre-Encoded Mechanism," in IEEE Access, vol. 8, pp. 114842-114853,
        2020, doi: 10.1109/ACCESS.2020.3003684

        Unsigned-multiplier architecture:
        G. W. Bewick, "Fast Multiplication: Algorithms and Implementations," PhD Thesis,
        Department of Electrical Engineering, Stanford University, 1994

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            booth [selection]
        
        This pass replaces multiplier cells with an implementation based on the Booth
        algorithm. It operates on $mul cells whose width of operands is at least 4x4
        and whose width of result is at least 8. The detailed architecture is selected
        from two options based on the signedness of the operands to the $mul cell.
        
        See the references below for the description of the architectures.
        
        Signed-multiplier architecture:
        Y. J. Chang, Y. C. Cheng, S. C. Liao and C. H. Hsiao, "A Low Power Radix-4 Booth
        Multiplier With Pre-Encoded Mechanism," in IEEE Access, vol. 8, pp. 114842-114853,
        2020, doi: 10.1109/ACCESS.2020.3003684
        
        Unsigned-multiplier architecture:
        G. W. Bewick, "Fast Multiplication: Algorithms and Implementations," PhD Thesis,
        Department of Electrical Engineering, Stanford University, 1994
        
