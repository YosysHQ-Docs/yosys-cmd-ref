===========================================
write_smt2 - write design to SMT-LIBv2 file
===========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_smt2`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_smt2 [options] [filename]

    ::

        Write a SMT-LIBv2 [1] description of the current design. For a module with name
        '<mod>' this will declare the sort '<mod>_s' (state of the module) and will
        define and declare functions operating on that state.

        The following SMT2 functions are generated for a module with name '<mod>'.
        Some declarations/definitions are printed with a special comment. A prover
        using the SMT2 files can use those comments to collect all relevant metadata
        about the design.

            ; yosys-smt2-module <mod>
            (declare-sort |<mod>_s| 0)
                The sort representing a state of module <mod>.

            (define-fun |<mod>_h| ((state |<mod>_s|)) Bool (...))
                This function must be asserted for each state to establish the
                design hierarchy.

            ; yosys-smt2-input <wirename> <width>
            ; yosys-smt2-output <wirename> <width>
            ; yosys-smt2-register <wirename> <width>
            ; yosys-smt2-wire <wirename> <width>
            (define-fun |<mod>_n <wirename>| (|<mod>_s|) (_ BitVec <width>))
            (define-fun |<mod>_n <wirename>| (|<mod>_s|) Bool)
                For each port, register, and wire with the 'keep' attribute set an
                accessor function is generated. Single-bit wires are returned as Bool,
                multi-bit wires as BitVec.

            ; yosys-smt2-cell <submod> <instancename>
            (declare-fun |<mod>_h <instancename>| (|<mod>_s|) |<submod>_s|)
                There is a function like that for each hierarchical instance. It
                returns the sort that represents the state of the sub-module that
                implements the instance.

            (declare-fun |<mod>_is| (|<mod>_s|) Bool)
                This function must be asserted 'true' for initial states, and 'false'
                otherwise.

            (define-fun |<mod>_i| ((state |<mod>_s|)) Bool (...))
                This function must be asserted 'true' for initial states. For
                non-initial states it must be left unconstrained.

            (define-fun |<mod>_t| ((state |<mod>_s|) (next_state |<mod>_s|)) Bool (...))
                This function evaluates to 'true' if the states 'state' and
                'next_state' form a valid state transition.

            (define-fun |<mod>_a| ((state |<mod>_s|)) Bool (...))
                This function evaluates to 'true' if all assertions hold in the state.

            (define-fun |<mod>_u| ((state |<mod>_s|)) Bool (...))
                This function evaluates to 'true' if all assumptions hold in the state.

            ; yosys-smt2-assert <id> <filename:linenum>
            (define-fun |<mod>_a <id>| ((state |<mod>_s|)) Bool (...))
                Each $assert cell is converted into one of this functions. The function
                evaluates to 'true' if the assert statement holds in the state.

            ; yosys-smt2-assume <id> <filename:linenum>
            (define-fun |<mod>_u <id>| ((state |<mod>_s|)) Bool (...))
                Each $assume cell is converted into one of this functions. The function
                evaluates to 'true' if the assume statement holds in the state.

            ; yosys-smt2-cover <id> <filename:linenum>
            (define-fun |<mod>_c <id>| ((state |<mod>_s|)) Bool (...))
                Each $cover cell is converted into one of this functions. The function
                evaluates to 'true' if the cover statement is activated in the state.

        Options:


    .. code:: yoscrypt

        -verbose

    ::

            this will print the recursive walk used to export the modules.


    .. code:: yoscrypt

        -stbv

    ::

            Use a BitVec sort to represent a state instead of an uninterpreted
            sort. As a side-effect this will prevent use of arrays to model
            memories.


    .. code:: yoscrypt

        -stdt

    ::

            Use SMT-LIB 2.6 style datatypes to represent a state instead of an
            uninterpreted sort.


    .. code:: yoscrypt

        -nobv

    ::

            disable support for BitVec (FixedSizeBitVectors theory). without this
            option multi-bit wires are represented using the BitVec sort and
            support for coarse grain cells (incl. arithmetic) is enabled.


    .. code:: yoscrypt

        -nomem

    ::

            disable support for memories (via ArraysEx theory). this option is
            implied by -nobv. only $mem cells without merged registers in
            read ports are supported. call "memory" with -nordff to make sure
            that no registers are merged into $mem read ports. '<mod>_m' functions
            will be generated for accessing the arrays that are used to represent
            memories.


    .. code:: yoscrypt

        -wires

    ::

            create '<mod>_n' functions for all public wires. by default only ports,
            registers, and wires with the 'keep' attribute are exported.


    .. code:: yoscrypt

        -tpl <template_file>

    ::

            use the given template file. the line containing only the token '%%'
            is replaced with the regular output of this command.


    .. code:: yoscrypt

        -solver-option <option> <value>

    ::

            emit a `; yosys-smt2-solver-option` directive for yosys-smtbmc to write
            the given option as a `(set-option ...)` command in the SMT-LIBv2.


    ::

        [1] For more information on SMT-LIBv2 visit http://smt-lib.org/ or read David
        R. Cok's tutorial: https://smtlib.github.io/jSMTLIB/SMTLIBTutorial.pdf

        ---------------------------------------------------------------------------

        Example:

        Consider the following module (test.v). We want to prove that the output can
        never transition from a non-zero value to a zero value.

                module test(input clk, output reg [3:0] y);
                  always @(posedge clk)
                    y <= (y << 1) | ^y;
                endmodule

        For this proof we create the following template (test.tpl).

                ; we need QF_UFBV for this proof
                (set-logic QF_UFBV)

                ; insert the auto-generated code here
                %%

                ; declare two state variables s1 and s2
                (declare-fun s1 () test_s)
                (declare-fun s2 () test_s)

                ; state s2 is the successor of state s1
                (assert (test_t s1 s2))

                ; we are looking for a model with y non-zero in s1
                (assert (distinct (|test_n y| s1) #b0000))

                ; we are looking for a model with y zero in s2
                (assert (= (|test_n y| s2) #b0000))

                ; is there such a model?
                (check-sat)

        The following yosys script will create a 'test.smt2' file for our proof:

                read_verilog test.v
                hierarchy -check; proc; opt; check -assert
                write_smt2 -bv -tpl test.tpl test.smt2

        Running 'cvc4 test.smt2' will print 'unsat' because y can never transition
        from non-zero to zero in the test design.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_smt2 [options] [filename]
        
        Write a SMT-LIBv2 [1] description of the current design. For a module with name
        '<mod>' this will declare the sort '<mod>_s' (state of the module) and will
        define and declare functions operating on that state.
        
        The following SMT2 functions are generated for a module with name '<mod>'.
        Some declarations/definitions are printed with a special comment. A prover
        using the SMT2 files can use those comments to collect all relevant metadata
        about the design.
        
            ; yosys-smt2-module <mod>
            (declare-sort |<mod>_s| 0)
                The sort representing a state of module <mod>.
        
            (define-fun |<mod>_h| ((state |<mod>_s|)) Bool (...))
                This function must be asserted for each state to establish the
                design hierarchy.
        
            ; yosys-smt2-input <wirename> <width>
            ; yosys-smt2-output <wirename> <width>
            ; yosys-smt2-register <wirename> <width>
            ; yosys-smt2-wire <wirename> <width>
            (define-fun |<mod>_n <wirename>| (|<mod>_s|) (_ BitVec <width>))
            (define-fun |<mod>_n <wirename>| (|<mod>_s|) Bool)
                For each port, register, and wire with the 'keep' attribute set an
                accessor function is generated. Single-bit wires are returned as Bool,
                multi-bit wires as BitVec.
        
            ; yosys-smt2-cell <submod> <instancename>
            (declare-fun |<mod>_h <instancename>| (|<mod>_s|) |<submod>_s|)
                There is a function like that for each hierarchical instance. It
                returns the sort that represents the state of the sub-module that
                implements the instance.
        
            (declare-fun |<mod>_is| (|<mod>_s|) Bool)
                This function must be asserted 'true' for initial states, and 'false'
                otherwise.
        
            (define-fun |<mod>_i| ((state |<mod>_s|)) Bool (...))
                This function must be asserted 'true' for initial states. For
                non-initial states it must be left unconstrained.
        
            (define-fun |<mod>_t| ((state |<mod>_s|) (next_state |<mod>_s|)) Bool (...))
                This function evaluates to 'true' if the states 'state' and
                'next_state' form a valid state transition.
        
            (define-fun |<mod>_a| ((state |<mod>_s|)) Bool (...))
                This function evaluates to 'true' if all assertions hold in the state.
        
            (define-fun |<mod>_u| ((state |<mod>_s|)) Bool (...))
                This function evaluates to 'true' if all assumptions hold in the state.
        
            ; yosys-smt2-assert <id> <filename:linenum>
            (define-fun |<mod>_a <id>| ((state |<mod>_s|)) Bool (...))
                Each $assert cell is converted into one of this functions. The function
                evaluates to 'true' if the assert statement holds in the state.
        
            ; yosys-smt2-assume <id> <filename:linenum>
            (define-fun |<mod>_u <id>| ((state |<mod>_s|)) Bool (...))
                Each $assume cell is converted into one of this functions. The function
                evaluates to 'true' if the assume statement holds in the state.
        
            ; yosys-smt2-cover <id> <filename:linenum>
            (define-fun |<mod>_c <id>| ((state |<mod>_s|)) Bool (...))
                Each $cover cell is converted into one of this functions. The function
                evaluates to 'true' if the cover statement is activated in the state.
        
        Options:
        
            -verbose
                this will print the recursive walk used to export the modules.
        
            -stbv
                Use a BitVec sort to represent a state instead of an uninterpreted
                sort. As a side-effect this will prevent use of arrays to model
                memories.
        
            -stdt
                Use SMT-LIB 2.6 style datatypes to represent a state instead of an
                uninterpreted sort.
        
            -nobv
                disable support for BitVec (FixedSizeBitVectors theory). without this
                option multi-bit wires are represented using the BitVec sort and
                support for coarse grain cells (incl. arithmetic) is enabled.
        
            -nomem
                disable support for memories (via ArraysEx theory). this option is
                implied by -nobv. only $mem cells without merged registers in
                read ports are supported. call "memory" with -nordff to make sure
                that no registers are merged into $mem read ports. '<mod>_m' functions
                will be generated for accessing the arrays that are used to represent
                memories.
        
            -wires
                create '<mod>_n' functions for all public wires. by default only ports,
                registers, and wires with the 'keep' attribute are exported.
        
            -tpl <template_file>
                use the given template file. the line containing only the token '%%'
                is replaced with the regular output of this command.
        
            -solver-option <option> <value>
                emit a `; yosys-smt2-solver-option` directive for yosys-smtbmc to write
                the given option as a `(set-option ...)` command in the SMT-LIBv2.
        
        [1] For more information on SMT-LIBv2 visit http://smt-lib.org/ or read David
        R. Cok's tutorial: https://smtlib.github.io/jSMTLIB/SMTLIBTutorial.pdf
        
        ---------------------------------------------------------------------------
        
        Example:
        
        Consider the following module (test.v). We want to prove that the output can
        never transition from a non-zero value to a zero value.
        
                module test(input clk, output reg [3:0] y);
                  always @(posedge clk)
                    y <= (y << 1) | ^y;
                endmodule
        
        For this proof we create the following template (test.tpl).
        
                ; we need QF_UFBV for this proof
                (set-logic QF_UFBV)
        
                ; insert the auto-generated code here
                %%
        
                ; declare two state variables s1 and s2
                (declare-fun s1 () test_s)
                (declare-fun s2 () test_s)
        
                ; state s2 is the successor of state s1
                (assert (test_t s1 s2))
        
                ; we are looking for a model with y non-zero in s1
                (assert (distinct (|test_n y| s1) #b0000))
        
                ; we are looking for a model with y zero in s2
                (assert (= (|test_n y| s2) #b0000))
        
                ; is there such a model?
                (check-sat)
        
        The following yosys script will create a 'test.smt2' file for our proof:
        
                read_verilog test.v
                hierarchy -check; proc; opt; check -assert
                write_smt2 -bv -tpl test.tpl test.smt2
        
        Running 'cvc4 test.smt2' will print 'unsat' because y can never transition
        from non-zero to zero in the test design.
        
