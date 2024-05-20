$divfloor
=========

.. cell:def:: $divfloor
   :title: $divfloor

   
       $divfloor (A, B, Y)
   
   Division with floored result (rounded towards negative infinity).

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1121

   module \$divfloor (A, B, Y);
       
       parameter A_SIGNED = 0;
       parameter B_SIGNED = 0;
       parameter A_WIDTH = 0;
       parameter B_WIDTH = 0;
       parameter Y_WIDTH = 0;
       
       input [A_WIDTH-1:0] A;
       input [B_WIDTH-1:0] B;
       output [Y_WIDTH-1:0] Y;
       
       generate
           if (A_SIGNED && B_SIGNED) begin:BLOCK1
               localparam WIDTH =
                       A_WIDTH >= B_WIDTH && A_WIDTH >= Y_WIDTH ? A_WIDTH :
                       B_WIDTH >= A_WIDTH && B_WIDTH >= Y_WIDTH ? B_WIDTH : Y_WIDTH;
               wire [WIDTH:0] A_buf, B_buf, N_buf;
               assign A_buf = $signed(A);
               assign B_buf = $signed(B);
               assign N_buf = (A[A_WIDTH-1] == B[B_WIDTH-1]) || A == 0 ? A_buf : $signed(A_buf - (B[B_WIDTH-1] ? B_buf+1 : B_buf-1));
               assign Y = $signed(N_buf) / $signed(B_buf);
           end else begin:BLOCK2
               assign Y = A / B;
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $divfloor``.
