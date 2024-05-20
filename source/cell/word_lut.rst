$lut
====

.. cell:def:: $lut
   :title: $lut

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1417

   module \$lut (A, Y);
       
       parameter WIDTH = 0;
       parameter LUT = 0;
       
       input [WIDTH-1:0] A;
       output Y;
       
       \$bmux #(.WIDTH(1), .S_WIDTH(WIDTH)) mux(.A(LUT[(1<<WIDTH)-1:0]), .S(A), .Y(Y));
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $lut``.
