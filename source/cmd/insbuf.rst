================================================
insbuf - insert buffer cells for connected wires
================================================

.. only:: html

    :code:`yosys> help insbuf`
    ----------------------------------------------------------------------------


    :code:`insbuf [options] [selection]` ::

        Insert buffer cells into the design for directly connected wires.


    :code:`-buf <celltype> <in-portname> <out-portname>` ::

            Use the given cell type instead of $_BUF_. (Notice that the next
            call to "clean" will remove all $_BUF_ in the design.)

.. only:: latex

    ::

        
            insbuf [options] [selection]
        
        Insert buffer cells into the design for directly connected wires.
        
            -buf <celltype> <in-portname> <out-portname>
                Use the given cell type instead of $_BUF_. (Notice that the next
                call to "clean" will remove all $_BUF_ in the design.)
        
