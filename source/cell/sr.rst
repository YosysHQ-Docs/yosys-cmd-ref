$sr
===

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1890

   module \$sr (SET, CLR, Q);
       
       parameter WIDTH = 0;
       parameter SET_POLARITY = 1'b1;
       parameter CLR_POLARITY = 1'b1;
       
       input [WIDTH-1:0] SET, CLR;
       output reg [WIDTH-1:0] Q;
       
       wire [WIDTH-1:0] pos_set = SET_POLARITY ? SET : ~SET;
       wire [WIDTH-1:0] pos_clr = CLR_POLARITY ? CLR : ~CLR;
       
       genvar i;
       generate
           for (i = 0; i < WIDTH; i = i+1) begin:bitslices
               always @*
                   if (pos_clr[i])
                       Q[i] <= 0;
                   else if (pos_set[i])
                       Q[i] <= 1;
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $sr``.
