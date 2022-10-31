===================================
fsm_detect - finding FSMs in design
===================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help fsm_detect`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        fsm_detect [selection]

    ::

        This pass detects finite state machines by identifying the state signal.
        The state signal is then marked by setting the attribute 'fsm_encoding'
        on the state signal to "auto".

        Existing 'fsm_encoding' attributes are not changed by this pass.

        Signals can be protected from being detected by this pass by setting the
        'fsm_encoding' attribute to "none".

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fsm_detect [selection]
        
        This pass detects finite state machines by identifying the state signal.
        The state signal is then marked by setting the attribute 'fsm_encoding'
        on the state signal to "auto".
        
        Existing 'fsm_encoding' attributes are not changed by this pass.
        
        Signals can be protected from being detected by this pass by setting the
        'fsm_encoding' attribute to "none".
        
