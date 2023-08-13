============================================
assertpmux - adds asserts for parallel muxes
============================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: assertpmux
    :title: adds asserts for parallel muxes



    .. code:: yoscrypt

        assertpmux [options] [selection]

    ::

        This command adds asserts to the design that assert that all parallel muxes
        ($pmux cells) have a maximum of one of their inputs enable at any time.


    .. code:: yoscrypt

        -noinit

    ::

            do not enforce the pmux condition during the init state


    .. code:: yoscrypt

        -always

    ::

            usually the $pmux condition is only checked when the $pmux output
            is used by the mux tree it drives. this option will deactivate this
            additional constraint and check the $pmux condition always.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            assertpmux [options] [selection]
        
        This command adds asserts to the design that assert that all parallel muxes
        ($pmux cells) have a maximum of one of their inputs enable at any time.
        
            -noinit
                do not enforce the pmux condition during the init state
        
            -always
                usually the $pmux condition is only checked when the $pmux output
                is used by the mux tree it drives. this option will deactivate this
                additional constraint and check the $pmux condition always.
        
