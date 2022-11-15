==============================================
equiv_miter - extract miter from equiv circuit
==============================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help equiv_miter`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        equiv_miter [options] miter_module [selection]

    ::

        This creates a miter module for further analysis of the selected $equiv cells.


    .. code:: yoscrypt

        -trigger

    ::

            Create a trigger output


    .. code:: yoscrypt

        -cmp

    ::

            Create cmp_* outputs for individual unproven $equiv cells


    .. code:: yoscrypt

        -assert

    ::

            Create a $assert cell for each unproven $equiv cell


    .. code:: yoscrypt

        -undef

    ::

            Create compare logic that handles undefs correctly

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            equiv_miter [options] miter_module [selection]
        
        This creates a miter module for further analysis of the selected $equiv cells.
        
            -trigger
                Create a trigger output
        
            -cmp
                Create cmp_* outputs for individual unproven $equiv cells
        
            -assert
                Create a $assert cell for each unproven $equiv cell
        
            -undef
                Create compare logic that handles undefs correctly
        
