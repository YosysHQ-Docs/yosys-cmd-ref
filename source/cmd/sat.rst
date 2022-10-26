========================================
sat - solve a SAT problem in the circuit
========================================

.. only:: html

    :code:`yosys> help sat`
    ----------------------------------------------------------------------------


    :code:`sat [options] [selection]` ::

        This command solves a SAT problem defined over the currently selected circuit
        and additional constraints passed as parameters.


    :code:`-all` ::

            show all solutions to the problem (this can grow exponentially, use
            -max <N> instead to get <N> solutions)


    :code:`-max <N>` ::

            like -all, but limit number of solutions to <N>


    :code:`-enable_undef` ::

            enable modeling of undef value (aka 'x-bits')
            this option is implied by -set-def, -set-undef et. cetera


    :code:`-max_undef` ::

            maximize the number of undef bits in solutions, giving a better
            picture of which input bits are actually vital to the solution.


    :code:`-set <signal> <value>` ::

            set the specified signal to the specified value.


    :code:`-set-def <signal>` ::

            add a constraint that all bits of the given signal must be defined


    :code:`-set-any-undef <signal>` ::

            add a constraint that at least one bit of the given signal is undefined


    :code:`-set-all-undef <signal>` ::

            add a constraint that all bits of the given signal are undefined


    :code:`-set-def-inputs` ::

            add -set-def constraints for all module inputs


    :code:`-show <signal>` ::

            show the model for the specified signal. if no -show option is
            passed then a set of signals to be shown is automatically selected.


    :code:`-show-inputs, -show-outputs, -show-ports` ::

            add all module (input/output) ports to the list of shown signals


    :code:`-show-regs, -show-public, -show-all` ::

            show all registers, show signals with 'public' names, show all signals


    :code:`-ignore_div_by_zero` ::

            ignore all solutions that involve a division by zero


    :code:`-ignore_unknown_cells` ::

            ignore all cells that can not be matched to a SAT model


    ::

        The following options can be used to set up a sequential problem:


    :code:`-seq <N>` ::

            set up a sequential problem with <N> time steps. The steps will
            be numbered from 1 to N.

            note: for large <N> it can be significantly faster to use
            -tempinduct-baseonly -maxsteps <N> instead of -seq <N>.


    :code:`-set-at <N> <signal> <value>`

    :code:`-unset-at <N> <signal>` ::

            set or unset the specified signal to the specified value in the
            given timestep. this has priority over a -set for the same signal.


    :code:`-set-assumes` ::

            set all assumptions provided via $assume cells


    :code:`-set-def-at <N> <signal>`

    :code:`-set-any-undef-at <N> <signal>`

    :code:`-set-all-undef-at <N> <signal>` ::

            add undef constraints in the given timestep.


    :code:`-set-init <signal> <value>` ::

            set the initial value for the register driving the signal to the value


    :code:`-set-init-undef` ::

            set all initial states (not set using -set-init) to undef


    :code:`-set-init-def` ::

            do not force a value for the initial state but do not allow undef


    :code:`-set-init-zero` ::

            set all initial states (not set using -set-init) to zero


    :code:`-dump_vcd <vcd-file-name>` ::

            dump SAT model (counter example in proof) to VCD file


    :code:`-dump_json <json-file-name>` ::

            dump SAT model (counter example in proof) to a WaveJSON file.


    :code:`-dump_cnf <cnf-file-name>` ::

            dump CNF of SAT problem (in DIMACS format). in temporal induction
            proofs this is the CNF of the first induction step.


    ::

        The following additional options can be used to set up a proof. If also -seq
        is passed, a temporal induction proof is performed.


    :code:`-tempinduct` ::

            Perform a temporal induction proof. In a temporal induction proof it is
            proven that the condition holds forever after the number of time steps
            specified using -seq.


    :code:`-tempinduct-def` ::

            Perform a temporal induction proof. Assume an initial state with all
            registers set to defined values for the induction step.


    :code:`-tempinduct-baseonly` ::

            Run only the basecase half of temporal induction (requires -maxsteps)


    :code:`-tempinduct-inductonly` ::

            Run only the induction half of temporal induction


    :code:`-tempinduct-skip <N>` ::

            Skip the first <N> steps of the induction proof.

            note: this will assume that the base case holds for <N> steps.
            this must be proven independently with "-tempinduct-baseonly
            -maxsteps <N>". Use -initsteps if you just want to set a
            minimal induction length.


    :code:`-prove <signal> <value>` ::

            Attempt to proof that <signal> is always <value>.


    :code:`-prove-x <signal> <value>` ::

            Like -prove, but an undef (x) bit in the lhs matches any value on
            the right hand side. Useful for equivalence checking.


    :code:`-prove-asserts` ::

            Prove that all asserts in the design hold.


    :code:`-prove-skip <N>` ::

            Do not enforce the prove-condition for the first <N> time steps.


    :code:`-maxsteps <N>` ::

            Set a maximum length for the induction.


    :code:`-initsteps <N>` ::

            Set initial length for the induction.
            This will speed up the search of the right induction length
            for deep induction proofs.


    :code:`-stepsize <N>` ::

            Increase the size of the induction proof in steps of <N>.
            This will speed up the search of the right induction length
            for deep induction proofs.


    :code:`-timeout <N>` ::

            Maximum number of seconds a single SAT instance may take.


    :code:`-verify` ::

            Return an error and stop the synthesis script if the proof fails.


    :code:`-verify-no-timeout` ::

            Like -verify but do not return an error for timeouts.


    :code:`-falsify` ::

            Return an error and stop the synthesis script if the proof succeeds.


    :code:`-falsify-no-timeout` ::

            Like -falsify but do not return an error for timeouts.

.. only:: latex

    ::

        
            sat [options] [selection]
        
        This command solves a SAT problem defined over the currently selected circuit
        and additional constraints passed as parameters.
        
            -all
                show all solutions to the problem (this can grow exponentially, use
                -max <N> instead to get <N> solutions)
        
            -max <N>
                like -all, but limit number of solutions to <N>
        
            -enable_undef
                enable modeling of undef value (aka 'x-bits')
                this option is implied by -set-def, -set-undef et. cetera
        
            -max_undef
                maximize the number of undef bits in solutions, giving a better
                picture of which input bits are actually vital to the solution.
        
            -set <signal> <value>
                set the specified signal to the specified value.
        
            -set-def <signal>
                add a constraint that all bits of the given signal must be defined
        
            -set-any-undef <signal>
                add a constraint that at least one bit of the given signal is undefined
        
            -set-all-undef <signal>
                add a constraint that all bits of the given signal are undefined
        
            -set-def-inputs
                add -set-def constraints for all module inputs
        
            -show <signal>
                show the model for the specified signal. if no -show option is
                passed then a set of signals to be shown is automatically selected.
        
            -show-inputs, -show-outputs, -show-ports
                add all module (input/output) ports to the list of shown signals
        
            -show-regs, -show-public, -show-all
                show all registers, show signals with 'public' names, show all signals
        
            -ignore_div_by_zero
                ignore all solutions that involve a division by zero
        
            -ignore_unknown_cells
                ignore all cells that can not be matched to a SAT model
        
        The following options can be used to set up a sequential problem:
        
            -seq <N>
                set up a sequential problem with <N> time steps. The steps will
                be numbered from 1 to N.
        
                note: for large <N> it can be significantly faster to use
                -tempinduct-baseonly -maxsteps <N> instead of -seq <N>.
        
            -set-at <N> <signal> <value>
            -unset-at <N> <signal>
                set or unset the specified signal to the specified value in the
                given timestep. this has priority over a -set for the same signal.
        
            -set-assumes
                set all assumptions provided via $assume cells
        
            -set-def-at <N> <signal>
            -set-any-undef-at <N> <signal>
            -set-all-undef-at <N> <signal>
                add undef constraints in the given timestep.
        
            -set-init <signal> <value>
                set the initial value for the register driving the signal to the value
        
            -set-init-undef
                set all initial states (not set using -set-init) to undef
        
            -set-init-def
                do not force a value for the initial state but do not allow undef
        
            -set-init-zero
                set all initial states (not set using -set-init) to zero
        
            -dump_vcd <vcd-file-name>
                dump SAT model (counter example in proof) to VCD file
        
            -dump_json <json-file-name>
                dump SAT model (counter example in proof) to a WaveJSON file.
        
            -dump_cnf <cnf-file-name>
                dump CNF of SAT problem (in DIMACS format). in temporal induction
                proofs this is the CNF of the first induction step.
        
        The following additional options can be used to set up a proof. If also -seq
        is passed, a temporal induction proof is performed.
        
            -tempinduct
                Perform a temporal induction proof. In a temporal induction proof it is
                proven that the condition holds forever after the number of time steps
                specified using -seq.
        
            -tempinduct-def
                Perform a temporal induction proof. Assume an initial state with all
                registers set to defined values for the induction step.
        
            -tempinduct-baseonly
                Run only the basecase half of temporal induction (requires -maxsteps)
        
            -tempinduct-inductonly
                Run only the induction half of temporal induction
        
            -tempinduct-skip <N>
                Skip the first <N> steps of the induction proof.
        
                note: this will assume that the base case holds for <N> steps.
                this must be proven independently with "-tempinduct-baseonly
                -maxsteps <N>". Use -initsteps if you just want to set a
                minimal induction length.
        
            -prove <signal> <value>
                Attempt to proof that <signal> is always <value>.
        
            -prove-x <signal> <value>
                Like -prove, but an undef (x) bit in the lhs matches any value on
                the right hand side. Useful for equivalence checking.
        
            -prove-asserts
                Prove that all asserts in the design hold.
        
            -prove-skip <N>
                Do not enforce the prove-condition for the first <N> time steps.
        
            -maxsteps <N>
                Set a maximum length for the induction.
        
            -initsteps <N>
                Set initial length for the induction.
                This will speed up the search of the right induction length
                for deep induction proofs.
        
            -stepsize <N>
                Increase the size of the induction proof in steps of <N>.
                This will speed up the search of the right induction length
                for deep induction proofs.
        
            -timeout <N>
                Maximum number of seconds a single SAT instance may take.
        
            -verify
                Return an error and stop the synthesis script if the proof fails.
        
            -verify-no-timeout
                Like -verify but do not return an error for timeouts.
        
            -falsify
                Return an error and stop the synthesis script if the proof succeeds.
        
            -falsify-no-timeout
                Like -falsify but do not return an error for timeouts.
        
