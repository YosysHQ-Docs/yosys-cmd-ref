==============================================
extract_fa - find and extract full/half adders
==============================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: extract_fa
    :title: find and extract full/half adders



    .. code:: yoscrypt

        extract_fa [options] [selection]

    ::

        This pass extracts full/half adders from a gate-level design.


    .. code:: yoscrypt

        -fa, -ha

    ::

            Enable cell types (fa=full adder, ha=half adder)
            All types are enabled if none of this options is used


    .. code:: yoscrypt

        -d <int>

    ::

            Set maximum depth for extracted logic cones (default=20)


    .. code:: yoscrypt

        -b <int>

    ::

            Set maximum breadth for extracted logic cones (default=6)


    .. code:: yoscrypt

        -v

    ::

            Verbose output

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            extract_fa [options] [selection]
        
        This pass extracts full/half adders from a gate-level design.
        
            -fa, -ha
                Enable cell types (fa=full adder, ha=half adder)
                All types are enabled if none of this options is used
        
            -d <int>
                Set maximum depth for extracted logic cones (default=20)
        
            -b <int>
                Set maximum breadth for extracted logic cones (default=6)
        
            -v
                Verbose output
        
