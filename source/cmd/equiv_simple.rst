==================================================
equiv_simple - try proving simple $equiv instances
==================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: equiv_simple
    :title: try proving simple $equiv instances



    .. code:: yoscrypt

        equiv_simple [options] [selection]

    ::

        This command tries to prove $equiv cells using a simple direct SAT approach.


    .. code:: yoscrypt

        -v

    ::

            verbose output


    .. code:: yoscrypt

        -undef

    ::

            enable modelling of undef states


    .. code:: yoscrypt

        -short

    ::

            create shorter input cones that stop at shared nodes. This yields
            simpler SAT problems but sometimes fails to prove equivalence.


    .. code:: yoscrypt

        -nogroup

    ::

            disabling grouping of $equiv cells by output wire


    .. code:: yoscrypt

        -seq <N>

    ::

            the max. number of time steps to be considered (default = 1)

.. raw:: latex

    \end{comment}

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
        
