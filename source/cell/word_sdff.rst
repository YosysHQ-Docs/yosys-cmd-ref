$sdff
=====

.. cell:def:: $sdff
   :title: $sdff

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2090

   module \$sdff (CLK, SRST, D, Q);
       
       parameter WIDTH = 0;
       parameter CLK_POLARITY = 1'b1;
       parameter SRST_POLARITY = 1'b1;
       parameter SRST_VALUE = 0;
       
       input CLK, SRST;
       input [WIDTH-1:0] D;
       output reg [WIDTH-1:0] Q;
       wire pos_clk = CLK == CLK_POLARITY;
       wire pos_srst = SRST == SRST_POLARITY;
       
       always @(posedge pos_clk) begin
           if (pos_srst)
               Q <= SRST_VALUE;
           else
               Q <= D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $sdff``.
