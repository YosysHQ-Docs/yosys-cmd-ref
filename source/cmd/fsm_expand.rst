======================================================
fsm_expand - expand FSM cells by merging logic into it
======================================================

.. only:: html

    :code:`yosys> help fsm_expand`
    ----------------------------------------------------------------------------


    :code:`fsm_expand [-full] [selection]` ::

        The fsm_extract pass is conservative about the cells that belong to a finite
        state machine. This pass can be used to merge additional auxiliary gates into
        the finite state machine.

        By default, fsm_expand is still a bit conservative regarding merging larger
        word-wide cells. Call with -full to consider all cells for merging.

.. only:: latex

    ::

        
            fsm_expand [-full] [selection]
        
        The fsm_extract pass is conservative about the cells that belong to a finite
        state machine. This pass can be used to merge additional auxiliary gates into
        the finite state machine.
        
        By default, fsm_expand is still a bit conservative regarding merging larger
        word-wide cells. Call with -full to consider all cells for merging.
        
