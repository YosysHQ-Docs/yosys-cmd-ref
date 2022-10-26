==================================================
equiv_simple - try proving simple $equiv instances
==================================================

.. only:: html

    :code:`yosys> help equiv_simple`
    ----------------------------------------------------------------------------


    :code:`equiv_simple [options] [selection]` ::

        This command tries to prove $equiv cells using a simple direct SAT approach.


    :code:`-v` ::

            verbose output


    :code:`-undef` ::

            enable modelling of undef states


    :code:`-short` ::

            create shorter input cones that stop at shared nodes. This yields
            simpler SAT problems but sometimes fails to prove equivalence.


    :code:`-nogroup` ::

            disabling grouping of $equiv cells by output wire


    :code:`-seq <N>` ::

            the max. number of time steps to be considered (default = 1)

.. only:: latex

    ::

        
            equiv_simple [options] [selection]
        
        This command tries to prove $equiv cells using a simple direct SAT approach.
        
            -v
                verbose output
        
            -undef
                enable modelling of undef states
        
            -short
                create shorter input cones that stop at shared nodes. This yields
                simpler SAT problems but sometimes fails to prove equivalence.
        
            -nogroup
                disabling grouping of $equiv cells by output wire
        
            -seq <N>
                the max. number of time steps to be considered (default = 1)
        
