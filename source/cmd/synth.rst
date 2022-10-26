================================
synth - generic synthesis script
================================

.. only:: html

    :code:`yosys> help synth`
    ----------------------------------------------------------------------------


    :code:`synth [options]` ::

        This command runs the default synthesis script. This command does not operate
        on partly selected designs.


    :code:`-top <module>` ::

            use the specified module as top module (default='top')


    :code:`-auto-top` ::

            automatically determine the top of the design hierarchy


    :code:`-flatten` ::

            flatten the design before synthesis. this will pass '-auto-top' to
            'hierarchy' if no top module is specified.


    :code:`-encfile <file>` ::

            passed to 'fsm_recode' via 'fsm'


    :code:`-lut <k>` ::

            perform synthesis for a k-LUT architecture.


    :code:`-nofsm` ::

            do not run FSM optimization


    :code:`-noabc` ::

            do not run abc (as if yosys was compiled without ABC support)


    :code:`-noalumacc` ::

            do not run 'alumacc' pass. i.e. keep arithmetic operators in
            their direct form ($add, $sub, etc.).


    :code:`-nordff` ::

            passed to 'memory'. prohibits merging of FFs into memory read ports


    :code:`-noshare` ::

            do not run SAT-based resource sharing


    :code:`-run <from_label>[:<to_label>]` ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    :code:`-abc9` ::

            use new ABC9 flow (EXPERIMENTAL)


    :code:`-flowmap` ::

            use FlowMap LUT techmapping instead of ABC


    :code:`-no-rw-check` ::

            marks all recognized read ports as "return don't-care value on
            read/write collision" (same result as setting the no_rw_check
            attribute on all memories).



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
                alumacc      (unless -noalumacc)
                share        (unless -noshare)
                opt
                memory -nomap
                opt_clean

            fine:
                opt -fast -full
                memory_map
                opt -full
                techmap
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
                alumacc      (unless -noalumacc)
                share        (unless -noshare)
                opt
                memory -nomap
                opt_clean
        
            fine:
                opt -fast -full
                memory_map
                opt -full
                techmap
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
        
