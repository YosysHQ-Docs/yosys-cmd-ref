$dffe
=====

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1956

   module \$dffe (CLK, EN, D, Q);
       
       parameter WIDTH = 0;
       parameter CLK_POLARITY = 1'b1;
       parameter EN_POLARITY = 1'b1;
       
       input CLK, EN;
       input [WIDTH-1:0] D;
       output reg [WIDTH-1:0] Q;
       wire pos_clk = CLK == CLK_POLARITY;
       
       always @(posedge pos_clk) begin
           if (EN == EN_POLARITY) Q <= D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $dffe``.
