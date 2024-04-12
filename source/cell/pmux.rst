$pmux
=====

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1362

   module \$pmux (A, B, S, Y);
       
       parameter WIDTH = 0;
       parameter S_WIDTH = 0;
       
       input [WIDTH-1:0] A;
       input [WIDTH*S_WIDTH-1:0] B;
       input [S_WIDTH-1:0] S;
       output reg [WIDTH-1:0] Y;
       
       integer i;
       reg found_active_sel_bit;
       
       always @* begin
           Y = A;
           found_active_sel_bit = 0;
           for (i = 0; i < S_WIDTH; i = i+1)
               case (S[i])
                   1'b1: begin
                       Y = found_active_sel_bit ? 'bx : B >> (WIDTH*i);
                       found_active_sel_bit = 1;
                   end
                   1'b0: ;
                   1'bx: begin
                       Y = 'bx;
                       found_active_sel_bit = 'bx;
                   end
               endcase
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $pmux``.
