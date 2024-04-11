====================================
ltp - print longest topological path
====================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: ltp
    :title: print longest topological path



    .. code:: yoscrypt

        ltp [options] [selection]

    ::

        This command prints the longest topological path in the design. (Only considers
        paths within a single module, so the design must be flattened.)


    .. code:: yoscrypt

        -noff

    ::

            automatically exclude FF cell types

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            ltp [options] [selection]
        
        This command prints the longest topological path in the design. (Only considers
        paths within a single module, so the design must be flattened.)
        
            -noff
                automatically exclude FF cell types
        
