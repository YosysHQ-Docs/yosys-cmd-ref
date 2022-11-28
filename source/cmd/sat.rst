========================================
sat - solve a SAT problem in the circuit
========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help sat`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        sat [options] [selection]

    ::

        This command solves a SAT problem defined over the currently selected circuit
        and additional constraints passed as parameters.


    .. code:: yoscrypt

        -all

    ::

            show all solutions to the problem (this can grow exponentially, use
            -max <N> instead to get <N> solutions)


    .. code:: yoscrypt

        -max <N>

    ::

            like -all, but limit number of solutions to <N>


    .. code:: yoscrypt

        -enable_undef

    ::

            enable modeling of undef value (aka 'x-bits')
            this option is implied by -set-def, -set-undef et. cetera


    .. code:: yoscrypt

        -max_undef

    ::

            maximize the number of undef bits in solutions, giving a better
            picture of which input bits are actually vital to the solution.


    .. code:: yoscrypt

        -set <signal> <value>

    ::

            set the specified signal to the specified value.


    .. code:: yoscrypt

        -set-def <signal>

    ::

            add a constraint that all bits of the given signal must be defined


    .. code:: yoscrypt

        -set-any-undef <signal>

    ::

            add a constraint that at least one bit of the given signal is undefined


    .. code:: yoscrypt

        -set-all-undef <signal>

    ::

            add a constraint that all bits of the given signal are undefined


    .. code:: yoscrypt

        -set-def-inputs

    ::

            add -set-def constraints for all module inputs


    .. code:: yoscrypt

        -set-def-formal

    ::

            add -set-def constraints for formal $anyinit, $anyconst, $anyseq cells


    .. code:: yoscrypt

        -show <signal>

    ::

            show the model for the specified signal. if no -show option is
            passed then a set of signals to be shown is automatically selected.


    .. code:: yoscrypt

        -show-inputs, -show-outputs, -show-ports

    ::

            add all module (input/output) ports to the list of shown signals


    .. code:: yoscrypt

        -show-regs, -show-public, -show-all

    ::

            show all registers, show signals with 'public' names, show all signals


    .. code:: yoscrypt

        -ignore_div_by_zero

    ::

            ignore all solutions that involve a division by zero


    .. code:: yoscrypt

        -ignore_unknown_cells

    ::

            ignore all cells that can not be matched to a SAT model


    ::

        The following options can be used to set up a sequential problem:


    .. code:: yoscrypt

        -seq <N>

    ::

            set up a sequential problem with <N> time steps. The steps will
            be numbered from 1 to N.

            note: for large <N> it can be significantly faster to use
            -tempinduct-baseonly -maxsteps <N> instead of -seq <N>.


    .. code:: yoscrypt

        -set-at <N> <signal> <value>

   

    .. code:: yoscrypt

        -unset-at <N> <signal>

    ::

            set or unset the specified signal to the specified value in the
            given timestep. this has priority over a -set for the same signal.


    .. code:: yoscrypt

        -set-assumes

    ::

            set all assumptions provided via $assume cells


    .. code:: yoscrypt

        -set-def-at <N> <signal>

   

    .. code:: yoscrypt

        -set-any-undef-at <N> <signal>

   

    .. code:: yoscrypt

        -set-all-undef-at <N> <signal>

    ::

            add undef constraints in the given timestep.


    .. code:: yoscrypt

        -set-init <signal> <value>

    ::

            set the initial value for the register driving the signal to the value


    .. code:: yoscrypt

        -set-init-undef

    ::

            set all initial states (not set using -set-init) to undef


    .. code:: yoscrypt

        -set-init-def

    ::

            do not force a value for the initial state but do not allow undef


    .. code:: yoscrypt

        -set-init-zero

    ::

            set all initial states (not set using -set-init) to zero


    .. code:: yoscrypt

        -dump_vcd <vcd-file-name>

    ::

            dump SAT model (counter example in proof) to VCD file


    .. code:: yoscrypt

        -dump_json <json-file-name>

    ::

            dump SAT model (counter example in proof) to a WaveJSON file.


    .. code:: yoscrypt

        -dump_cnf <cnf-file-name>

    ::

            dump CNF of SAT problem (in DIMACS format). in temporal induction
            proofs this is the CNF of the first induction step.


    ::

        The following additional options can be used to set up a proof. If also -seq
        is passed, a temporal induction proof is performed.


    .. code:: yoscrypt

        -tempinduct

    ::

            Perform a temporal induction proof. In a temporal induction proof it is
            proven that the condition holds forever after the number of time steps
            specified using -seq.


    .. code:: yoscrypt

        -tempinduct-def

    ::

            Perform a temporal induction proof. Assume an initial state with all
            registers set to defined values for the induction step.


    .. code:: yoscrypt

        -tempinduct-baseonly

    ::

            Run only the basecase half of temporal induction (requires -maxsteps)


    .. code:: yoscrypt

        -tempinduct-inductonly

    ::

            Run only the induction half of temporal induction


    .. code:: yoscrypt

        -tempinduct-skip <N>

    ::

            Skip the first <N> steps of the induction proof.

            note: this will assume that the base case holds for <N> steps.
            this must be proven independently with "-tempinduct-baseonly
            -maxsteps <N>". Use -initsteps if you just want to set a
            minimal induction length.


    .. code:: yoscrypt

        -prove <signal> <value>

    ::

            Attempt to proof that <signal> is always <value>.


    .. code:: yoscrypt

        -prove-x <signal> <value>

    ::

            Like -prove, but an undef (x) bit in the lhs matches any value on
            the right hand side. Useful for equivalence checking.


    .. code:: yoscrypt

        -prove-asserts

    ::

            Prove that all asserts in the design hold.


    .. code:: yoscrypt

        -prove-skip <N>

    ::

            Do not enforce the prove-condition for the first <N> time steps.


    .. code:: yoscrypt

        -maxsteps <N>

    ::

            Set a maximum length for the induction.


    .. code:: yoscrypt

        -initsteps <N>

    ::

            Set initial length for the induction.
            This will speed up the search of the right induction length
            for deep induction proofs.


    .. code:: yoscrypt

        -stepsize <N>

    ::

            Increase the size of the induction proof in steps of <N>.
            This will speed up the search of the right induction length
            for deep induction proofs.


    .. code:: yoscrypt

        -timeout <N>

    ::

            Maximum number of seconds a single SAT instance may take.


    .. code:: yoscrypt

        -verify

    ::

            Return an error and stop the synthesis script if the proof fails.


    .. code:: yoscrypt

        -verify-no-timeout

    ::

            Like -verify but do not return an error for timeouts.


    .. code:: yoscrypt

        -falsify

    ::

            Return an error and stop the synthesis script if the proof succeeds.


    .. code:: yoscrypt

        -falsify-no-timeout

    ::

            Like -falsify but do not return an error for timeouts.

.. raw:: latex

    \end{comment}

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
        
            -set-def-formal
                add -set-def constraints for formal $anyinit, $anyconst, $anyseq cells
        
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
        
