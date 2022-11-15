========================================
fsm_opt - optimize finite state machines
========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help fsm_opt`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        fsm_opt [selection]

    ::

        This pass optimizes FSM cells. It detects which output signals are actually
        not used and removes them from the FSM. This pass is usually used in
        combination with the 'opt_clean' pass (see also 'help fsm').

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fsm_opt [selection]
        
        This pass optimizes FSM cells. It detects which output signals are actually
        not used and removes them from the FSM. This pass is usually used in
        combination with the 'opt_clean' pass (see also 'help fsm').
        
