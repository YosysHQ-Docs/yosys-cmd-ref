$slice
======

.. cell:def:: $slice
   :title: $slice

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1291

   module \$slice (A, Y);
       
       parameter OFFSET = 0;
       parameter A_WIDTH = 0;
       parameter Y_WIDTH = 0;
       
       input [A_WIDTH-1:0] A;
       output [Y_WIDTH-1:0] Y;
       
       assign Y = A >> OFFSET;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $slice``.
