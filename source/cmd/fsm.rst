================================================
fsm - extract and optimize finite state machines
================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: fsm
    :title: extract and optimize finite state machines



    .. code:: yoscrypt

        fsm [options] [selection]

    ::

        This pass calls all the other fsm_* passes in a useful order. This performs
        FSM extraction and optimization. It also calls opt_clean as needed:

            fsm_detect          unless got option -nodetect
            fsm_extract

            fsm_opt
            opt_clean
            fsm_opt

            fsm_expand          if got option -expand
            opt_clean           if got option -expand
            fsm_opt             if got option -expand

            fsm_recode          unless got option -norecode

            fsm_info

            fsm_export          if got option -export
            fsm_map             unless got option -nomap

        Options:


    .. code:: yoscrypt

        -expand, -norecode, -export, -nomap

    ::

            enable or disable passes as indicated above


    .. code:: yoscrypt

        -fullexpand

    ::

            call expand with -full option


    .. code:: yoscrypt

        -encoding type

   

    .. code:: yoscrypt

        -fm_set_fsm_file file

   

    .. code:: yoscrypt

        -encfile file

    ::

            passed through to fsm_recode pass


    ::

        This pass uses a subset of FF types to detect FSMs. Run 'opt -nosdff -nodffe'
        before this pass to prepare the design.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            fsm [options] [selection]
        
        This pass calls all the other fsm_* passes in a useful order. This performs
        FSM extraction and optimization. It also calls opt_clean as needed:
        
            fsm_detect          unless got option -nodetect
            fsm_extract
        
            fsm_opt
            opt_clean
            fsm_opt
        
            fsm_expand          if got option -expand
            opt_clean           if got option -expand
            fsm_opt             if got option -expand
        
            fsm_recode          unless got option -norecode
        
            fsm_info
        
            fsm_export          if got option -export
            fsm_map             unless got option -nomap
        
        Options:
        
            -expand, -norecode, -export, -nomap
                enable or disable passes as indicated above
        
            -fullexpand
                call expand with -full option
        
            -encoding type
            -fm_set_fsm_file file
            -encfile file
                passed through to fsm_recode pass
        
        This pass uses a subset of FF types to detect FSMs. Run 'opt -nosdff -nodffe'
        before this pass to prepare the design.
        
