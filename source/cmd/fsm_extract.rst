=======================================
fsm_extract - extracting FSMs in design
=======================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help fsm_extract`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        fsm_extract [selection]

    ::

        This pass operates on all signals marked as FSM state signals using the
        'fsm_encoding' attribute. It consumes the logic that creates the state signal
        and uses the state signal to generate control signal and replaces it with an
        FSM cell.

        The generated FSM cell still generates the original state signal with its
        original encoding. The 'fsm_opt' pass can be used in combination with the
        'opt_clean' pass to eliminate this signal.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fsm_extract [selection]
        
        This pass operates on all signals marked as FSM state signals using the
        'fsm_encoding' attribute. It consumes the logic that creates the state signal
        and uses the state signal to generate control signal and replaces it with an
        FSM cell.
        
        The generated FSM cell still generates the original state signal with its
        original encoding. The 'fsm_opt' pass can be used in combination with the
        'opt_clean' pass to eliminate this signal.
        
