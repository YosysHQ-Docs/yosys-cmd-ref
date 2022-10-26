=====================================================
async2sync - convert async FF inputs to sync circuits
=====================================================

.. only:: html

    :code:`yosys> help async2sync`
    ----------------------------------------------------------------------------


    :code:`async2sync [options] [selection]` ::

        This command replaces async FF inputs with sync circuits emulating the same
        behavior for when the async signals are actually synchronized to the clock.

        This pass assumes negative hold time for the async FF inputs. For example when
        a reset deasserts with the clock edge, then the FF output will still drive the
        reset value in the next cycle regardless of the data-in value at the time of
        the clock edge.

.. only:: latex

    ::

        
            async2sync [options] [selection]
        
        This command replaces async FF inputs with sync circuits emulating the same
        behavior for when the async signals are actually synchronized to the clock.
        
        This pass assumes negative hold time for the async FF inputs. For example when
        a reset deasserts with the clock edge, then the FF output will still drive the
        reset value in the next cycle regardless of the data-in value at the time of
        the clock edge.
        
