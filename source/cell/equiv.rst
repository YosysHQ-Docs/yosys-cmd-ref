$equiv
======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1829

   module \$equiv (A, B, Y);
       
       input A, B;
       output Y;
       
       assign Y = (A !== 1'bx && A !== B) ? 1'bx : A;
       
       `ifndef SIMLIB_NOCHECKS
       always @* begin
           if (A !== 1'bx && A !== B) begin
               $display("Equivalence failed!");
               $stop;
           end
       end
       `endif
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $equiv``.
