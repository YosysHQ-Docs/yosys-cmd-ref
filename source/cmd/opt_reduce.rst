==================================================
opt_reduce - simplify large MUXes and AND/OR gates
==================================================

.. only:: html

    :code:`yosys> help opt_reduce`
    ----------------------------------------------------------------------------


    :code:`opt_reduce [options] [selection]` ::

        This pass performs two interlinked optimizations:

        1. it consolidates trees of large AND gates or OR gates and eliminates
        duplicated inputs.

        2. it identifies duplicated inputs to MUXes and replaces them with a single
        input with the original control signals OR'ed together.


    :code:`-fine` ::

          perform fine-grain optimizations


    :code:`-full` ::

          alias for -fine

.. only:: latex

    ::

        
            opt_reduce [options] [selection]
        
        This pass performs two interlinked optimizations:
        
        1. it consolidates trees of large AND gates or OR gates and eliminates
        duplicated inputs.
        
        2. it identifies duplicated inputs to MUXes and replaces them with a single
        input with the original control signals OR'ed together.
        
            -fine
              perform fine-grain optimizations
        
            -full
              alias for -fine
        
