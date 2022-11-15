==========================================
memory - translate memories to basic cells
==========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help memory`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        memory [-norom] [-nomap] [-nordff] [-nowiden] [-nosat] [-memx] [-no-rw-check] [-bram <bram_rules>] [selection]

    ::

        This pass calls all the other memory_* passes in a useful order:

            opt_mem
            opt_mem_priority
            opt_mem_feedback
            memory_bmux2rom                     (skipped if called with -norom)
            memory_dff [-no-rw-check]           (skipped if called with -nordff or -memx)
            opt_clean
            memory_share [-nowiden] [-nosat]
            opt_mem_widen
            memory_memx                         (when called with -memx)
            opt_clean
            memory_collect
            memory_bram -rules <bram_rules>     (when called with -bram)
            memory_map                          (skipped if called with -nomap)

        This converts memories to word-wide DFFs and address decoders
        or multiport memory blocks if called with the -nomap option.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            memory [-norom] [-nomap] [-nordff] [-nowiden] [-nosat] [-memx] [-no-rw-check] [-bram <bram_rules>] [selection]
        
        This pass calls all the other memory_* passes in a useful order:
        
            opt_mem
            opt_mem_priority
            opt_mem_feedback
            memory_bmux2rom                     (skipped if called with -norom)
            memory_dff [-no-rw-check]           (skipped if called with -nordff or -memx)
            opt_clean
            memory_share [-nowiden] [-nosat]
            opt_mem_widen
            memory_memx                         (when called with -memx)
            opt_clean
            memory_collect
            memory_bram -rules <bram_rules>     (when called with -bram)
            memory_map                          (skipped if called with -nomap)
        
        This converts memories to word-wide DFFs and address decoders
        or multiport memory blocks if called with the -nomap option.
        
