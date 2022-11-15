===========================================
fsm_recode - recoding finite state machines
===========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help fsm_recode`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        fsm_recode [options] [selection]

    ::

        This pass reassign the state encodings for FSM cells. At the moment only
        one-hot encoding and binary encoding is supported.
            -encoding <type>
                specify the encoding scheme used for FSMs without the
                'fsm_encoding' attribute or with the attribute set to `auto'.


    .. code:: yoscrypt

        -fm_set_fsm_file <file>

    ::

            generate a file containing the mapping from old to new FSM encoding
            in form of Synopsys Formality set_fsm_* commands.


    .. code:: yoscrypt

        -encfile <file>

    ::

            write the mappings from old to new FSM encoding to a file in the
            following format:

                .fsm <module_name> <state_signal>
                .map <old_bitpattern> <new_bitpattern>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fsm_recode [options] [selection]
        
        This pass reassign the state encodings for FSM cells. At the moment only
        one-hot encoding and binary encoding is supported.
            -encoding <type>
                specify the encoding scheme used for FSMs without the
                'fsm_encoding' attribute or with the attribute set to `auto'.
        
            -fm_set_fsm_file <file>
                generate a file containing the mapping from old to new FSM encoding
                in form of Synopsys Formality set_fsm_* commands.
        
            -encfile <file>
                write the mappings from old to new FSM encoding to a file in the
                following format:
        
                    .fsm <module_name> <state_signal>
                    .map <old_bitpattern> <new_bitpattern>
        
