$aldffe
=======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2139

   module \$aldffe (CLK, ALOAD, AD, EN, D, Q);
       
       parameter WIDTH = 0;
       parameter CLK_POLARITY = 1'b1;
       parameter EN_POLARITY = 1'b1;
       parameter ALOAD_POLARITY = 1'b1;
       
       input CLK, ALOAD, EN;
       input [WIDTH-1:0] D;
       input [WIDTH-1:0] AD;
       output reg [WIDTH-1:0] Q;
       wire pos_clk = CLK == CLK_POLARITY;
       wire pos_aload = ALOAD == ALOAD_POLARITY;
       
       always @(posedge pos_clk, posedge pos_aload) begin
           if (pos_aload)
               Q <= AD;
           else if (EN == EN_POLARITY)
               Q <= D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $aldffe``.
