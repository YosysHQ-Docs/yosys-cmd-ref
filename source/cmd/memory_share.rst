=======================================
memory_share - consolidate memory ports
=======================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: memory_share
    :title: consolidate memory ports



    .. code:: yoscrypt

        memory_share [-nosat] [-nowiden] [selection]

    ::

        This pass merges share-able memory ports into single memory ports.

        The following methods are used to consolidate the number of memory ports:

          - When multiple write ports access the same address then this is converted
            to a single write port with a more complex data and/or enable logic path.

          - When multiple read or write ports access adjacent aligned addresses, they
            are merged to a single wide read or write port.  This transformation can be
            disabled with the "-nowiden" option.

          - When multiple write ports are never accessed at the same time (a SAT
            solver is used to determine this), then the ports are merged into a single
            write port.  This transformation can be disabled with the "-nosat" option.

        Note that in addition to the algorithms implemented in this pass, the $memrd
        and $memwr cells are also subject to generic resource sharing passes (and other
        optimizations) such as "share" and "opt_merge".

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            memory_share [-nosat] [-nowiden] [selection]
        
        This pass merges share-able memory ports into single memory ports.
        
        The following methods are used to consolidate the number of memory ports:
        
          - When multiple write ports access the same address then this is converted
            to a single write port with a more complex data and/or enable logic path.
        
          - When multiple read or write ports access adjacent aligned addresses, they
            are merged to a single wide read or write port.  This transformation can be
            disabled with the "-nowiden" option.
        
          - When multiple write ports are never accessed at the same time (a SAT
            solver is used to determine this), then the ports are merged into a single
            write port.  This transformation can be disabled with the "-nosat" option.
        
        Note that in addition to the algorithms implemented in this pass, the $memrd
        and $memwr cells are also subject to generic resource sharing passes (and other
        optimizations) such as "share" and "opt_merge".
        
