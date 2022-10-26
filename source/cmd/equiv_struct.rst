==============================================
equiv_struct - structural equivalence checking
==============================================

.. only:: html

    :code:`yosys> help equiv_struct`
    ----------------------------------------------------------------------------


    :code:`equiv_struct [options] [selection]` ::

        This command adds additional $equiv cells based on the assumption that the
        gold and gate circuit are structurally equivalent. Note that this can introduce
        bad $equiv cells in cases where the netlists are not structurally equivalent,
        for example when analyzing circuits with cells with commutative inputs. This
        command will also de-duplicate gates.


    :code:`-fwd` ::

            by default this command performans forward sweeps until nothing can
            be merged by forwards sweeps, then backward sweeps until forward
            sweeps are effective again. with this option set only forward sweeps
            are performed.


    :code:`-fwonly <cell_type>` ::

            add the specified cell type to the list of cell types that are only
            merged in forward sweeps and never in backward sweeps. $equiv is in
            this list automatically.


    :code:`-icells` ::

            by default, the internal RTL and gate cell types are ignored. add
            this option to also process those cell types with this command.


    :code:`-maxiter <N>` ::

            maximum number of iterations to run before aborting

.. only:: latex

    ::

        
            equiv_struct [options] [selection]
        
        This command adds additional $equiv cells based on the assumption that the
        gold and gate circuit are structurally equivalent. Note that this can introduce
        bad $equiv cells in cases where the netlists are not structurally equivalent,
        for example when analyzing circuits with cells with commutative inputs. This
        command will also de-duplicate gates.
        
            -fwd
                by default this command performans forward sweeps until nothing can
                be merged by forwards sweeps, then backward sweeps until forward
                sweeps are effective again. with this option set only forward sweeps
                are performed.
        
            -fwonly <cell_type>
                add the specified cell type to the list of cell types that are only
                merged in forward sweeps and never in backward sweeps. $equiv is in
                this list automatically.
        
            -icells
                by default, the internal RTL and gate cell types are ignored. add
                this option to also process those cell types with this command.
        
            -maxiter <N>
                maximum number of iterations to run before aborting
        
