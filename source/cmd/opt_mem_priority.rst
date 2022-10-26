=======================================================================================
opt_mem_priority - remove priority relations between write ports that can never collide
=======================================================================================

.. only:: html

    :code:`yosys> help opt_mem_priority`
    ----------------------------------------------------------------------------


    :code:`opt_mem_priority [selection]` ::

        This pass detects cases where one memory write port has priority over another
        even though they can never collide with each other -- ie. there can never be
        a situation where a given memory bit is written by both ports at the same
        time, for example because of always-different addresses, or mutually exclusive
        enable signals. In such cases, the priority relation is removed.

.. only:: latex

    ::

        
            opt_mem_priority [selection]
        
        This pass detects cases where one memory write port has priority over another
        even though they can never collide with each other -- ie. there can never be
        a situation where a given memory bit is written by both ports at the same
        time, for example because of always-different addresses, or mutually exclusive
        enable signals. In such cases, the priority relation is removed.
        
