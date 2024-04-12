$anyinit
========

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1788

   module \$anyinit (D, Q);
       
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] D;
       output reg [WIDTH-1:0] Q;
       
       initial Q <= 'bx;
       
       always @(`SIMLIB_GLOBAL_CLOCK) begin
           Q <= D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $anyinit``.
