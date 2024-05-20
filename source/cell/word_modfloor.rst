$modfloor
=========

.. cell:def:: $modfloor
   :title: $modfloor

   
       $modfloor (A, B, Y)
   
   Modulo/remainder of division with floored result (rounded towards negative infinity).
   
   Invariant: $divfloor(A, B) * B + $modfloor(A, B) == A

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1160

   module \$modfloor (A, B, Y);
       
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
               localparam WIDTH = B_WIDTH >= Y_WIDTH ? B_WIDTH : Y_WIDTH;
               wire [WIDTH-1:0] B_buf, Y_trunc;
               assign B_buf = $signed(B);
               assign Y_trunc = $signed(A) % $signed(B);
               // flooring mod is the same as truncating mod for positive division results (A and B have
               // the same sign), as well as when there's no remainder.
               // For all other cases, they behave as `floor - trunc = B`
               assign Y = (A[A_WIDTH-1] == B[B_WIDTH-1]) || Y_trunc == 0 ? Y_trunc : $signed(B_buf) + $signed(Y_trunc);
           end else begin:BLOCK2
               // no difference between truncating and flooring for unsigned
               assign Y = A % B;
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $modfloor``.
