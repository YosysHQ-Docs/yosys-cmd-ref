$shift
======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:470

   module \$shift (A, B, Y);
       
       parameter A_SIGNED = 0;
       parameter B_SIGNED = 0;
       parameter A_WIDTH = 0;
       parameter B_WIDTH = 0;
       parameter Y_WIDTH = 0;
       
       input [A_WIDTH-1:0] A;
       input [B_WIDTH-1:0] B;
       output [Y_WIDTH-1:0] Y;
       
       generate
           if (A_SIGNED) begin:BLOCK1
               if (B_SIGNED) begin:BLOCK2
                   assign Y = $signed(B) < 0 ? $signed(A) << -B : $signed(A) >> B;
               end else begin:BLOCK3
                   assign Y = $signed(A) >> B;
               end
           end else begin:BLOCK4
               if (B_SIGNED) begin:BLOCK5
                   assign Y = $signed(B) < 0 ? A << -B : A >> B;
               end else begin:BLOCK6
                   assign Y = A >> B;
               end
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $shift``.
