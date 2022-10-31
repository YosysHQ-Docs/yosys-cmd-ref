====================================================
fmcombine - combine two instances of a cell into one
====================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help fmcombine`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        fmcombine [options] module_name gold_cell gate_cell

    ::

        This pass takes two cells, which are instances of the same module, and replaces
        them with one instance of a special 'combined' module, that effectively
        contains two copies of the original module, plus some formal properties.

        This is useful for formal test benches that check what differences in behavior
        a slight difference in input causes in a module.


    .. code:: yoscrypt

        -initeq

    ::

            Insert assumptions that initially all FFs in both circuits have the
            same initial values.


    .. code:: yoscrypt

        -anyeq

    ::

            Do not duplicate $anyseq/$anyconst cells.


    .. code:: yoscrypt

        -fwd

    ::

            Insert forward hint assumptions into the combined module.


    .. code:: yoscrypt

        -bwd

    ::

            Insert backward hint assumptions into the combined module.
            (Backward hints are logically equivalend to fordward hits, but
            some solvers are faster with bwd hints, or even both -bwd and -fwd.)


    .. code:: yoscrypt

        -nop

    ::

            Don't insert hint assumptions into the combined module.
            (This should not provide any speedup over the original design, but
            strangely sometimes it does.)


    ::

        If none of -fwd, -bwd, and -nop is given, then -fwd is used as default.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fmcombine [options] module_name gold_cell gate_cell
        
        This pass takes two cells, which are instances of the same module, and replaces
        them with one instance of a special 'combined' module, that effectively
        contains two copies of the original module, plus some formal properties.
        
        This is useful for formal test benches that check what differences in behavior
        a slight difference in input causes in a module.
        
            -initeq
                Insert assumptions that initially all FFs in both circuits have the
                same initial values.
        
            -anyeq
                Do not duplicate $anyseq/$anyconst cells.
        
            -fwd
                Insert forward hint assumptions into the combined module.
        
            -bwd
                Insert backward hint assumptions into the combined module.
                (Backward hints are logically equivalend to fordward hits, but
                some solvers are faster with bwd hints, or even both -bwd and -fwd.)
        
            -nop
                Don't insert hint assumptions into the combined module.
                (This should not provide any speedup over the original design, but
                strangely sometimes it does.)
        
        If none of -fwd, -bwd, and -nop is given, then -fwd is used as default.
        
