===================================
fsm_detect - finding FSMs in design
===================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: fsm_detect
    :title: finding FSMs in design



    .. code:: yoscrypt

        fsm_detect [options] [selection]

    ::

        This pass detects finite state machines by identifying the state signal.
        The state signal is then marked by setting the attribute 'fsm_encoding'
        on the state signal to "auto".


    .. code:: yoscrypt

        -ignore-self-reset

    ::

            Mark FSMs even if they are self-resetting


    ::

        Existing 'fsm_encoding' attributes are not changed by this pass.

        Signals can be protected from being detected by this pass by setting the
        'fsm_encoding' attribute to "none".

        This pass uses a subset of FF types to detect FSMs. Run 'opt -nosdff -nodffe'
        before this pass to prepare the design for fsm_detect.

        The Verific frontend may optimize the design in a way that interferes with FSM
        detection. Run 'verific -cfg db_infer_wide_muxes_post_elaboration 0' before
        reading the source, and 'bmuxmap -pmux' after 'proc' for best results.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fsm_detect [options] [selection]
        
        This pass detects finite state machines by identifying the state signal.
        The state signal is then marked by setting the attribute 'fsm_encoding'
        on the state signal to "auto".
        
            -ignore-self-reset
                Mark FSMs even if they are self-resetting
        
        Existing 'fsm_encoding' attributes are not changed by this pass.
        
        Signals can be protected from being detected by this pass by setting the
        'fsm_encoding' attribute to "none".
        
        This pass uses a subset of FF types to detect FSMs. Run 'opt -nosdff -nodffe'
        before this pass to prepare the design for fsm_detect.
        
        The Verific frontend may optimize the design in a way that interferes with FSM
        detection. Run 'verific -cfg db_infer_wide_muxes_post_elaboration 0' before
        reading the source, and 'bmuxmap -pmux' after 'proc' for best results.
        
