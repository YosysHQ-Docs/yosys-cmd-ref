=========================================
torder - print cells in topological order
=========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: torder
    :title: print cells in topological order



    .. code:: yoscrypt

        torder [options] [selection]

    ::

        This command prints the selected cells in topological order.


    .. code:: yoscrypt

        -stop <cell_type> <cell_port>

    ::

            do not use the specified cell port in topological sorting


    .. code:: yoscrypt

        -noautostop

    ::

            by default Q outputs of internal FF cells and memory read port outputs
            are not used in topological sorting. this option deactivates that.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            torder [options] [selection]
        
        This command prints the selected cells in topological order.
        
            -stop <cell_type> <cell_port>
                do not use the specified cell port in topological sorting
        
            -noautostop
                by default Q outputs of internal FF cells and memory read port outputs
                are not used in topological sorting. this option deactivates that.
        
