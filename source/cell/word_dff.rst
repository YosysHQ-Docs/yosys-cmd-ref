$dff
====

.. cell:def:: $dff
   :title: $dff

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1938

   module \$dff (CLK, D, Q);
       
       parameter WIDTH = 0;
       parameter CLK_POLARITY = 1'b1;
       
       input CLK;
       input [WIDTH-1:0] D;
       output reg [WIDTH-1:0] Q;
       wire pos_clk = CLK == CLK_POLARITY;
       
       always @(posedge pos_clk) begin
           Q <= D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $dff``.
