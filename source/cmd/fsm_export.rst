==========================================
fsm_export - exporting FSMs to KISS2 files
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: fsm_export
    :title: exporting FSMs to KISS2 files



    .. code:: yoscrypt

        fsm_export [-noauto] [-o filename] [-origenc] [selection]

    ::

        This pass creates a KISS2 file for every selected FSM. For FSMs with the
        'fsm_export' attribute set, the attribute value is used as filename, otherwise
        the module and cell name is used as filename. If the parameter '-o' is given,
        the first exported FSM is written to the specified filename. This overwrites
        the setting as specified with the 'fsm_export' attribute. All other FSMs are
        exported to the default name as mentioned above.


    .. code:: yoscrypt

        -noauto

    ::

            only export FSMs that have the 'fsm_export' attribute set


    .. code:: yoscrypt

        -o filename

    ::

            filename of the first exported FSM


    .. code:: yoscrypt

        -origenc

    ::

            use binary state encoding as state names instead of s0, s1, ...

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fsm_export [-noauto] [-o filename] [-origenc] [selection]
        
        This pass creates a KISS2 file for every selected FSM. For FSMs with the
        'fsm_export' attribute set, the attribute value is used as filename, otherwise
        the module and cell name is used as filename. If the parameter '-o' is given,
        the first exported FSM is written to the specified filename. This overwrites
        the setting as specified with the 'fsm_export' attribute. All other FSMs are
        exported to the default name as mentioned above.
        
            -noauto
                only export FSMs that have the 'fsm_export' attribute set
        
            -o filename
                filename of the first exported FSM
        
            -origenc
                use binary state encoding as state names instead of s0, s1, ...
        
