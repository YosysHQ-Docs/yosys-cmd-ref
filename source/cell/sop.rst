$sop
====

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1432

   module \$sop (A, Y);
       
       parameter WIDTH = 0;
       parameter DEPTH = 0;
       parameter TABLE = 0;
       
       input [WIDTH-1:0] A;
       output reg Y;
       
       integer i, j;
       reg match;
       
       always @* begin
           Y = 0;
           for (i = 0; i < DEPTH; i=i+1) begin
               match = 1;
               for (j = 0; j < WIDTH; j=j+1) begin
                   if (TABLE[2*WIDTH*i + 2*j + 0] && A[j]) match = 0;
                   if (TABLE[2*WIDTH*i + 2*j + 1] && !A[j]) match = 0;
               end
               if (match) Y = 1;
           end
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $sop``.
