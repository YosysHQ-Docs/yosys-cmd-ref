===========================================
fsm_recode - recoding finite state machines
===========================================

.. only:: html

    :code:`yosys> help fsm_recode`
    ----------------------------------------------------------------------------


    :code:`fsm_recode [options] [selection]` ::

        This pass reassign the state encodings for FSM cells. At the moment only
        one-hot encoding and binary encoding is supported.
            -encoding <type>
                specify the encoding scheme used for FSMs without the
                'fsm_encoding' attribute or with the attribute set to `auto'.


    :code:`-fm_set_fsm_file <file>` ::

            generate a file containing the mapping from old to new FSM encoding
            in form of Synopsys Formality set_fsm_* commands.


    :code:`-encfile <file>` ::

            write the mappings from old to new FSM encoding to a file in the
            following format:

                .fsm <module_name> <state_signal>
                .map <old_bitpattern> <new_bitpattern>

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
        
