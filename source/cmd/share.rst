==========================================
share - perform sat-based resource sharing
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: share
    :title: perform sat-based resource sharing



    .. code:: yoscrypt

        share [options] [selection]

    ::

        This pass merges shareable resources into a single resource. A SAT solver
        is used to determine if two resources are share-able.


    .. code:: yoscrypt

        -force

    ::

          Per default the selection of cells that is considered for sharing is
          narrowed using a list of cell types. With this option all selected
          cells are considered for resource sharing.

          IMPORTANT NOTE: If the -all option is used then no cells with internal
          state must be selected!


    .. code:: yoscrypt

        -aggressive

    ::

          Per default some heuristics are used to reduce the number of cells
          considered for resource sharing to only large resources. This options
          turns this heuristics off, resulting in much more cells being considered
          for resource sharing.


    .. code:: yoscrypt

        -fast

    ::

          Only consider the simple part of the control logic in SAT solving, resulting
          in much easier SAT problems at the cost of maybe missing some opportunities
          for resource sharing.


    .. code:: yoscrypt

        -limit N

    ::

          Only perform the first N merges, then stop. This is useful for debugging.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            share [options] [selection]
        
        This pass merges shareable resources into a single resource. A SAT solver
        is used to determine if two resources are share-able.
        
          -force
            Per default the selection of cells that is considered for sharing is
            narrowed using a list of cell types. With this option all selected
            cells are considered for resource sharing.
        
            IMPORTANT NOTE: If the -all option is used then no cells with internal
            state must be selected!
        
          -aggressive
            Per default some heuristics are used to reduce the number of cells
            considered for resource sharing to only large resources. This options
            turns this heuristics off, resulting in much more cells being considered
            for resource sharing.
        
          -fast
            Only consider the simple part of the control logic in SAT solving, resulting
            in much easier SAT problems at the cost of maybe missing some opportunities
            for resource sharing.
        
          -limit N
            Only perform the first N merges, then stop. This is useful for debugging.
        
