================================
synth - generic synthesis script
================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth [options]

    ::

        This command runs the default synthesis script. This command does not operate
        on partly selected designs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module (default='top')


    .. code:: yoscrypt

        -auto-top

    ::

            automatically determine the top of the design hierarchy


    .. code:: yoscrypt

        -flatten

    ::

            flatten the design before synthesis. this will pass '-auto-top' to
            'hierarchy' if no top module is specified.


    .. code:: yoscrypt

        -encfile <file>

    ::

            passed to 'fsm_recode' via 'fsm'


    .. code:: yoscrypt

        -lut <k>

    ::

            perform synthesis for a k-LUT architecture.


    .. code:: yoscrypt

        -nofsm

    ::

            do not run FSM optimization


    .. code:: yoscrypt

        -noabc

    ::

            do not run abc (as if yosys was compiled without ABC support)


    .. code:: yoscrypt

        -booth

    ::

            run the booth pass to map $mul to Booth encoded multipliers


    .. code:: yoscrypt

        -noalumacc

    ::

            do not run 'alumacc' pass. i.e. keep arithmetic operators in
            their direct form ($add, $sub, etc.).


    .. code:: yoscrypt

        -nordff

    ::

            passed to 'memory'. prohibits merging of FFs into memory read ports


    .. code:: yoscrypt

        -noshare

    ::

            do not run SAT-based resource sharing


    .. code:: yoscrypt

        -run <from_label>[:<to_label>]

    ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -abc9

    ::

            use new ABC9 flow (EXPERIMENTAL)


    .. code:: yoscrypt

        -flowmap

    ::

            use FlowMap LUT techmapping instead of ABC


    .. code:: yoscrypt

        -no-rw-check

    ::

            marks all recognized read ports as "return don't-care value on
            read/write collision" (same result as setting the no_rw_check
            attribute on all memories).


    .. code:: yoscrypt

        -extra-map filename

    ::

            source extra rules from the given file to complement the default
            mapping library in the `techmap` step. this option can be
            repeated.


    ::

        The following commands are executed by this synthesis command:

            begin:
                hierarchy -check [-top <top> | -auto-top]

            coarse:
                proc
                flatten      (if -flatten)
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm          (unless -nofsm)
                opt
                wreduce
                peepopt
                opt_clean
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v     (if -lut)
                booth        (if -booth)
                alumacc      (unless -noalumacc)
                share        (unless -noshare)
                opt
                memory -nomap
                opt_clean

            fine:
                opt -fast -full
                memory_map
                opt -full
                techmap                      (unless -extra-map)
                techmap -map +/techmap.v -map <inject>      (if -extra-map)
                techmap -map +/gate2lut.v    (if -noabc and -lut)
                clean; opt_lut               (if -noabc and -lut)
                flowmap -maxlut K            (if -flowmap and -lut)
                opt -fast
                abc -fast           (unless -noabc, unless -lut)
                abc -fast -lut k    (unless -noabc, if -lut)
                opt -fast           (unless -noabc)

            check:
                hierarchy -check
                stat
                check

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth [options]
        
        This command runs the default synthesis script. This command does not operate
        on partly selected designs.
        
            -top <module>
                use the specified module as top module (default='top')
        
            -auto-top
                automatically determine the top of the design hierarchy
        
            -flatten
                flatten the design before synthesis. this will pass '-auto-top' to
                'hierarchy' if no top module is specified.
        
            -encfile <file>
                passed to 'fsm_recode' via 'fsm'
        
            -lut <k>
                perform synthesis for a k-LUT architecture.
        
            -nofsm
                do not run FSM optimization
        
            -noabc
                do not run abc (as if yosys was compiled without ABC support)
        
            -booth
                run the booth pass to map $mul to Booth encoded multipliers
        
            -noalumacc
                do not run 'alumacc' pass. i.e. keep arithmetic operators in
                their direct form ($add, $sub, etc.).
        
            -nordff
                passed to 'memory'. prohibits merging of FFs into memory read ports
        
            -noshare
                do not run SAT-based resource sharing
        
            -run <from_label>[:<to_label>]
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -abc9
                use new ABC9 flow (EXPERIMENTAL)
        
            -flowmap
                use FlowMap LUT techmapping instead of ABC
        
            -no-rw-check
                marks all recognized read ports as "return don't-care value on
                read/write collision" (same result as setting the no_rw_check
                attribute on all memories).
        
            -extra-map filename
                source extra rules from the given file to complement the default
                mapping library in the `techmap` step. this option can be
                repeated.
        
        The following commands are executed by this synthesis command:
        
            begin:
                hierarchy -check [-top <top> | -auto-top]
        
            coarse:
                proc
                flatten      (if -flatten)
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm          (unless -nofsm)
                opt
                wreduce
                peepopt
                opt_clean
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v     (if -lut)
                booth        (if -booth)
                alumacc      (unless -noalumacc)
                share        (unless -noshare)
                opt
                memory -nomap
                opt_clean
        
            fine:
                opt -fast -full
                memory_map
                opt -full
                techmap                      (unless -extra-map)
                techmap -map +/techmap.v -map <inject>      (if -extra-map)
                techmap -map +/gate2lut.v    (if -noabc and -lut)
                clean; opt_lut               (if -noabc and -lut)
                flowmap -maxlut K            (if -flowmap and -lut)
                opt -fast
                abc -fast           (unless -noabc, unless -lut)
                abc -fast -lut k    (unless -noabc, if -lut)
                opt -fast           (unless -noabc)
        
            check:
                hierarchy -check
                stat
                check
        
