================================================
qbfsat - solve a 2QBF-SAT problem in the circuit
================================================

.. only:: html

    :code:`yosys> help qbfsat`
    ----------------------------------------------------------------------------


    :code:`qbfsat [options] [selection]` ::

        This command solves an "exists-forall" 2QBF-SAT problem defined over the
        currently selected module. Existentially-quantified variables are declared by
        assigning a wire "$anyconst". Universally-quantified variables may be
        explicitly declared by assigning a wire "$allconst", but module inputs will be
        treated as universally-quantified variables by default.


    :code:`-nocleanup` ::

            Do not delete temporary files and directories. Useful for debugging.


    :code:`-dump-final-smt2 <file>` ::

            Pass the --dump-smt2 option to yosys-smtbmc.


    :code:`-assume-outputs` ::

            Add an "$assume" cell for the conjunction of all one-bit module output
            wires.


    :code:`-assume-negative-polarity` ::

            When adding $assume cells for one-bit module output wires, assume they
            are negative polarity signals and should always be low, for example like
            the miters created with the `miter` command.


    :code:`-nooptimize` ::

            Ignore "\minimize" and "\maximize" attributes, do not emit
            "(maximize)" or "(minimize)" in the SMT-LIBv2, and generally make no
            attempt to optimize anything.


    :code:`-nobisection` ::

            If a wire is marked with the "\minimize" or "\maximize" attribute,
            do not attempt to optimize that value with the default iterated solving
            and threshold bisection approach. Instead, have yosys-smtbmc emit a
            "(minimize)" or "(maximize)" command in the SMT-LIBv2 output and
            hope that the solver supports optimizing quantified bitvector problems.


    :code:`-solver <solver>` ::

            Use a particular solver. Choose one of: "z3", "yices", and "cvc4".
            (default: yices)


    :code:`-solver-option <name> <value>` ::

            Set the specified solver option in the SMT-LIBv2 problem file.


    :code:`-timeout <value>` ::

            Set the per-iteration timeout in seconds.
            (default: no timeout)


    :code:`-O0, -O1, -O2` ::

            Control the use of ABC to simplify the QBF-SAT problem before solving.


    :code:`-sat` ::

            Generate an error if the solver does not return "sat".


    :code:`-unsat` ::

            Generate an error if the solver does not return "unsat".


    :code:`-show-smtbmc` ::

            Print the output from yosys-smtbmc.


    :code:`-specialize` ::

            If the problem is satisfiable, replace each "$anyconst" cell with its
            corresponding constant value from the model produced by the solver.


    :code:`-specialize-from-file <solution file>` ::

            Do not run the solver, but instead only attempt to replace each
            "$anyconst" cell in the current module with a constant value provided
            by the specified file.


    :code:`-write-solution <solution file>` ::

            If the problem is satisfiable, write the corresponding constant value
            for each "$anyconst" cell from the model produced by the solver to the
            specified file.

.. only:: latex

    ::

        
            qbfsat [options] [selection]
        
        This command solves an "exists-forall" 2QBF-SAT problem defined over the
        currently selected module. Existentially-quantified variables are declared by
        assigning a wire "$anyconst". Universally-quantified variables may be
        explicitly declared by assigning a wire "$allconst", but module inputs will be
        treated as universally-quantified variables by default.
        
            -nocleanup
                Do not delete temporary files and directories. Useful for debugging.
        
            -dump-final-smt2 <file>
                Pass the --dump-smt2 option to yosys-smtbmc.
        
            -assume-outputs
                Add an "$assume" cell for the conjunction of all one-bit module output
                wires.
        
            -assume-negative-polarity
                When adding $assume cells for one-bit module output wires, assume they
                are negative polarity signals and should always be low, for example like
                the miters created with the `miter` command.
        
            -nooptimize
                Ignore "\minimize" and "\maximize" attributes, do not emit
                "(maximize)" or "(minimize)" in the SMT-LIBv2, and generally make no
                attempt to optimize anything.
        
            -nobisection
                If a wire is marked with the "\minimize" or "\maximize" attribute,
                do not attempt to optimize that value with the default iterated solving
                and threshold bisection approach. Instead, have yosys-smtbmc emit a
                "(minimize)" or "(maximize)" command in the SMT-LIBv2 output and
                hope that the solver supports optimizing quantified bitvector problems.
        
            -solver <solver>
                Use a particular solver. Choose one of: "z3", "yices", and "cvc4".
                (default: yices)
        
            -solver-option <name> <value>
                Set the specified solver option in the SMT-LIBv2 problem file.
        
            -timeout <value>
                Set the per-iteration timeout in seconds.
                (default: no timeout)
        
            -O0, -O1, -O2
                Control the use of ABC to simplify the QBF-SAT problem before solving.
        
            -sat
                Generate an error if the solver does not return "sat".
        
            -unsat
                Generate an error if the solver does not return "unsat".
        
            -show-smtbmc
                Print the output from yosys-smtbmc.
        
            -specialize
                If the problem is satisfiable, replace each "$anyconst" cell with its
                corresponding constant value from the model produced by the solver.
        
            -specialize-from-file <solution file>
                Do not run the solver, but instead only attempt to replace each
                "$anyconst" cell in the current module with a constant value provided
                by the specified file.
        
            -write-solution <solution file>
                If the problem is satisfiable, write the corresponding constant value
                for each "$anyconst" cell from the model produced by the solver to the
                specified file.
        
