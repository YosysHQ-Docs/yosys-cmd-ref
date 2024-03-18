=================================
formalff - prepare FFs for formal
=================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: formalff
    :title: prepare FFs for formal



    .. code:: yoscrypt

        formalff [options] [selection]

    ::

        This pass transforms clocked flip-flops to prepare a design for formal
        verification. If a design contains latches and/or multiple different clocks run
        the async2sync or clk2fflogic passes before using this pass.


    .. code:: yoscrypt

        -clk2ff

    ::

            Replace all clocked flip-flops with $ff cells that use the implicit
            global clock. This assumes, without checking, that the design uses a
            single global clock. If that is not the case, the clk2fflogic pass
            should be used instead.


    .. code:: yoscrypt

        -ff2anyinit

    ::

            Replace uninitialized bits of $ff cells with $anyinit cells. An
            $anyinit cell behaves exactly like an $ff cell with an undefined
            initialization value. The difference is that $anyinit inhibits
            don't-care optimizations and is used to track solver-provided values
            in witness traces.

            If combined with -clk2ff this also affects newly created $ff cells.


    .. code:: yoscrypt

        -anyinit2ff

    ::

            Replaces $anyinit cells with uninitialized $ff cells. This performs the
            reverse of -ff2anyinit and can be used, before running a backend pass
            (or similar) that is not yet aware of $anyinit cells.

            Note that after running -anyinit2ff, in general, performing don't-care
            optimizations is not sound in a formal verification setting.


    .. code:: yoscrypt

        -fine

    ::

            Emit fine-grained $_FF_ cells instead of coarse-grained $ff cells for
            -anyinit2ff. Cannot be combined with -clk2ff or -ff2anyinit.


    .. code:: yoscrypt

        -setundef

    ::

            Find FFs with undefined initialization values for which changing the
            initialization does not change the observable behavior and initialize
            them. For -ff2anyinit, this reduces the number of generated $anyinit
            cells that drive wires with private names.


    .. code:: yoscrypt

        -hierarchy

    ::

            Propagates the 'replaced_by_gclk' attribute set by clk2ff upwards
            through the design hierarchy towards the toplevel inputs. This option
            works on the whole design and ignores the selection.


    .. code:: yoscrypt

        -assume

    ::

            Add assumptions that constrain wires with the 'replaced_by_gclk'
            attribute to the value they would have before an active clock edge.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            formalff [options] [selection]
        
        This pass transforms clocked flip-flops to prepare a design for formal
        verification. If a design contains latches and/or multiple different clocks run
        the async2sync or clk2fflogic passes before using this pass.
        
            -clk2ff
                Replace all clocked flip-flops with $ff cells that use the implicit
                global clock. This assumes, without checking, that the design uses a
                single global clock. If that is not the case, the clk2fflogic pass
                should be used instead.
        
            -ff2anyinit
                Replace uninitialized bits of $ff cells with $anyinit cells. An
                $anyinit cell behaves exactly like an $ff cell with an undefined
                initialization value. The difference is that $anyinit inhibits
                don't-care optimizations and is used to track solver-provided values
                in witness traces.
        
                If combined with -clk2ff this also affects newly created $ff cells.
        
            -anyinit2ff
                Replaces $anyinit cells with uninitialized $ff cells. This performs the
                reverse of -ff2anyinit and can be used, before running a backend pass
                (or similar) that is not yet aware of $anyinit cells.
        
                Note that after running -anyinit2ff, in general, performing don't-care
                optimizations is not sound in a formal verification setting.
        
            -fine
                Emit fine-grained $_FF_ cells instead of coarse-grained $ff cells for
                -anyinit2ff. Cannot be combined with -clk2ff or -ff2anyinit.
        
            -setundef
                Find FFs with undefined initialization values for which changing the
                initialization does not change the observable behavior and initialize
                them. For -ff2anyinit, this reduces the number of generated $anyinit
                cells that drive wires with private names.
        
            -hierarchy
                Propagates the 'replaced_by_gclk' attribute set by clk2ff upwards
                through the design hierarchy towards the toplevel inputs. This option
                works on the whole design and ignores the selection.
        
            -assume
                Add assumptions that constrain wires with the 'replaced_by_gclk'
                attribute to the value they would have before an active clock edge.
        
