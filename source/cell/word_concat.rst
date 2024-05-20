$concat
=======

.. cell:def:: $concat
   :title: $concat

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1306

   module \$concat (A, B, Y);
       
       parameter A_WIDTH = 0;
       parameter B_WIDTH = 0;
       
       input [A_WIDTH-1:0] A;
       input [B_WIDTH-1:0] B;
       output [A_WIDTH+B_WIDTH-1:0] Y;
       
       assign Y = {B, A};
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $concat``.
