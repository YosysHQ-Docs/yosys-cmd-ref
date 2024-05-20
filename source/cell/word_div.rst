$div
====

.. cell:def:: $div
   :title: $div

   
       $div (A, B, Y)
   
   Division with truncated result (rounded towards 0).

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1059

   module \$div (A, B, Y);
       
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
               assign Y = $signed(A) / $signed(B);
           end else begin:BLOCK2
               assign Y = A / B;
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $div``.
