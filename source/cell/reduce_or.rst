$reduce_or
==========


    $reduce_or (A, Y)

An OR reduction. This corresponds to the Verilog unary prefix '|' operator.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:271

   module \$reduce_or (A, Y);
       
       parameter A_SIGNED = 0;
       parameter A_WIDTH = 0;
       parameter Y_WIDTH = 0;
       
       input [A_WIDTH-1:0] A;
       output [Y_WIDTH-1:0] Y;
       
       generate
           if (A_SIGNED) begin:BLOCK1
               assign Y = |$signed(A);
           end else begin:BLOCK2
               assign Y = |A;
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $reduce_or``.
