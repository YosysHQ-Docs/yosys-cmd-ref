================================================
insbuf - insert buffer cells for connected wires
================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: insbuf
    :title: insert buffer cells for connected wires



    .. code:: yoscrypt

        insbuf [options] [selection]

    ::

        Insert buffer cells into the design for directly connected wires.


    .. code:: yoscrypt

        -buf <celltype> <in-portname> <out-portname>

    ::

            Use the given cell type instead of $_BUF_. (Notice that the next
            call to "clean" will remove all $_BUF_ in the design.)


    .. code:: yoscrypt

        -chain

    ::

            Chain buffer cells

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            insbuf [options] [selection]
        
        Insert buffer cells into the design for directly connected wires.
        
            -buf <celltype> <in-portname> <out-portname>
                Use the given cell type instead of $_BUF_. (Notice that the next
                call to "clean" will remove all $_BUF_ in the design.)
        
            -chain
                Chain buffer cells
        
