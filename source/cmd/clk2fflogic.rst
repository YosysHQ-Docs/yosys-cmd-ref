======================================================
clk2fflogic - convert clocked FFs to generic $ff cells
======================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help clk2fflogic`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        clk2fflogic [options] [selection]

    ::

        This command replaces clocked flip-flops with generic $ff cells that use the
        implicit global clock. This is useful for formal verification of designs with
        multiple clocks.

        This pass assumes negative hold time for the async FF inputs. For example when
        a reset deasserts with the clock edge, then the FF output will still drive the
        reset value in the next cycle regardless of the data-in value at the time of
        the clock edge.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            clk2fflogic [options] [selection]
        
        This command replaces clocked flip-flops with generic $ff cells that use the
        implicit global clock. This is useful for formal verification of designs with
        multiple clocks.
        
        This pass assumes negative hold time for the async FF inputs. For example when
        a reset deasserts with the clock edge, then the FF output will still drive the
        reset value in the next cycle regardless of the data-in value at the time of
        the clock edge.
        
