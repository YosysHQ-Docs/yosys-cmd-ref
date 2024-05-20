$ff
===

.. cell:def:: $ff
   :title: $ff

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1922

   module \$ff (D, Q);
       
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] D;
       output reg [WIDTH-1:0] Q;
       
       always @(`SIMLIB_GLOBAL_CLOCK) begin
           Q <= D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $ff``.
