=======================================================
opt_muxtree - eliminate dead trees in multiplexer trees
=======================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help opt_muxtree`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        opt_muxtree [selection]

    ::

        This pass analyzes the control signals for the multiplexer trees in the design
        and identifies inputs that can never be active. It then removes this dead
        branches from the multiplexer trees.

        This pass only operates on completely selected modules without processes.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            opt_muxtree [selection]
        
        This pass analyzes the control signals for the multiplexer trees in the design
        and identifies inputs that can never be active. It then removes this dead
        branches from the multiplexer trees.
        
        This pass only operates on completely selected modules without processes.
        
