===========================================================
memory_dff - merge input/output DFFs into memory read ports
===========================================================

.. only:: html

    :code:`yosys> help memory_dff`
    ----------------------------------------------------------------------------


    :code:`memory_dff [-no-rw-check] [selection]` ::

        This pass detects DFFs at memory read ports and merges them into the memory
        port. I.e. it consumes an asynchronous memory port and the flip-flops at its
        interface and yields a synchronous memory port.


    :code:`-no-rw-check` ::

            marks all recognized read ports as "return don't-care value on
            read/write collision" (same result as setting the no_rw_check
            attribute on all memories).

.. only:: latex

    ::

        
            memory_dff [-no-rw-check] [selection]
        
        This pass detects DFFs at memory read ports and merges them into the memory
        port. I.e. it consumes an asynchronous memory port and the flip-flops at its
        interface and yields a synchronous memory port.
        
            -no-rw-check
                marks all recognized read ports as "return don't-care value on
                read/write collision" (same result as setting the no_rw_check
                attribute on all memories).
        
