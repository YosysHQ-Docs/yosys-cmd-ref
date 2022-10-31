==================================================
opt_reduce - simplify large MUXes and AND/OR gates
==================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help opt_reduce`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        opt_reduce [options] [selection]

    ::

        This pass performs two interlinked optimizations:

        1. it consolidates trees of large AND gates or OR gates and eliminates
        duplicated inputs.

        2. it identifies duplicated inputs to MUXes and replaces them with a single
        input with the original control signals OR'ed together.


    .. code:: yoscrypt

        -fine

    ::

          perform fine-grain optimizations


    .. code:: yoscrypt

        -full

    ::

          alias for -fine

.. raw:: latex

    \end{comment}

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
        
