$bwmux
======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1667

   module \$bwmux (A, B, S, Y);
       
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] A, B;
       input [WIDTH-1:0] S;
       output [WIDTH-1:0] Y;
       
       genvar i;
       generate
           for (i = 0; i < WIDTH; i = i + 1) begin:slices
               assign Y[i] = S[i] ? B[i] : A[i];
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $bwmux``.
