============================================================
equiv_induct - proving $equiv cells using temporal induction
============================================================

.. only:: html

    :code:`yosys> help equiv_induct`
    ----------------------------------------------------------------------------


    :code:`equiv_induct [options] [selection]` ::

        Uses a version of temporal induction to prove $equiv cells.

        Only selected $equiv cells are proven and only selected cells are used to
        perform the proof.


    :code:`-undef` ::

            enable modelling of undef states


    :code:`-seq <N>` ::

            the max. number of time steps to be considered (default = 4)


    ::

        This command is very effective in proving complex sequential circuits, when
        the internal state of the circuit quickly propagates to $equiv cells.

        However, this command uses a weak definition of 'equivalence': This command
        proves that the two circuits will not diverge after they produce equal
        outputs (observable points via $equiv) for at least <N> cycles (the <N>
        specified via -seq).

        Combined with simulation this is very powerful because simulation can give
        you confidence that the circuits start out synced for at least <N> cycles
        after reset.

.. only:: latex

    ::

        
            equiv_induct [options] [selection]
        
        Uses a version of temporal induction to prove $equiv cells.
        
        Only selected $equiv cells are proven and only selected cells are used to
        perform the proof.
        
            -undef
                enable modelling of undef states
        
            -seq <N>
                the max. number of time steps to be considered (default = 4)
        
        This command is very effective in proving complex sequential circuits, when
        the internal state of the circuit quickly propagates to $equiv cells.
        
        However, this command uses a weak definition of 'equivalence': This command
        proves that the two circuits will not diverge after they produce equal
        outputs (observable points via $equiv) for at least <N> cycles (the <N>
        specified via -seq).
        
        Combined with simulation this is very powerful because simulation can give
        you confidence that the circuits start out synced for at least <N> cycles
        after reset.
        
