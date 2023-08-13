==============================================
memory_unpack - unpack multi-port memory cells
==============================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: memory_unpack
    :title: unpack multi-port memory cells



    .. code:: yoscrypt

        memory_unpack [selection]

    ::

        This pass converts the multi-port $mem memory cells into individual $memrd and
        $memwr cells. It is the counterpart to the memory_collect pass.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            memory_unpack [selection]
        
        This pass converts the multi-port $mem memory cells into individual $memrd and
        $memwr cells. It is the counterpart to the memory_collect pass.
        
