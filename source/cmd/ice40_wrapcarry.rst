=====================================
ice40_wrapcarry - iCE40: wrap carries
=====================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help ice40_wrapcarry`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        ice40_wrapcarry [selection]

    ::

        Wrap manually instantiated SB_CARRY cells, along with their associated SB_LUT4s,
        into an internal $__ICE40_CARRY_WRAPPER cell for preservation across technology
        mapping.

        Attributes on both cells will have their names prefixed with 'SB_CARRY.' or
        'SB_LUT4.' and attached to the wrapping cell.
        A (* keep *) attribute on either cell will be logically OR-ed together.


    .. code:: yoscrypt

        -unwrap

    ::

            unwrap $__ICE40_CARRY_WRAPPER cells back into SB_CARRYs and SB_LUT4s,
            including restoring their attributes.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            ice40_wrapcarry [selection]
        
        Wrap manually instantiated SB_CARRY cells, along with their associated SB_LUT4s,
        into an internal $__ICE40_CARRY_WRAPPER cell for preservation across technology
        mapping.
        
        Attributes on both cells will have their names prefixed with 'SB_CARRY.' or
        'SB_LUT4.' and attached to the wrapping cell.
        A (* keep *) attribute on either cell will be logically OR-ed together.
        
            -unwrap
                unwrap $__ICE40_CARRY_WRAPPER cells back into SB_CARRYs and SB_LUT4s,
                including restoring their attributes.
        
