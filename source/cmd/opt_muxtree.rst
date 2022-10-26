=======================================================
opt_muxtree - eliminate dead trees in multiplexer trees
=======================================================

.. only:: html

    :code:`yosys> help opt_muxtree`
    ----------------------------------------------------------------------------


    :code:`opt_muxtree [selection]` ::

        This pass analyzes the control signals for the multiplexer trees in the design
        and identifies inputs that can never be active. It then removes this dead
        branches from the multiplexer trees.

        This pass only operates on completely selected modules without processes.

.. only:: latex

    ::

        
            opt_muxtree [selection]
        
        This pass analyzes the control signals for the multiplexer trees in the design
        and identifies inputs that can never be active. It then removes this dead
        branches from the multiplexer trees.
        
        This pass only operates on completely selected modules without processes.
        
