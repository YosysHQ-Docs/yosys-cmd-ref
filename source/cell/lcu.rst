$lcu
====


    $lcu (P, G, CI, CO)

Lookahead carry unit
A building block dedicated to fast computation of carry-bits used in binary
arithmetic operations. By replacing the ripple carry structure used in full-adder
blocks, the more significant  bits of the sum can be expected to be computed more
quickly.
Typically created during `techmap` of $alu cells (see the "_90_alu" rule in
+/techmap.v).
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:554

   module \$lcu (P, G, CI, CO);
       
       parameter WIDTH = 1;
       
       input [WIDTH-1:0] P;    // Propagate
       input [WIDTH-1:0] G;    // Generate
       input CI;               // Carry-in
       
       output reg [WIDTH-1:0] CO; // Carry-out
       
       integer i;
       always @* begin
           CO = 'bx;
           if (^{P, G, CI} !== 1'bx) begin
               CO[0] = G[0] || (P[0] && CI);
               for (i = 1; i < WIDTH; i = i+1)
                   CO[i] = G[i] || (P[i] && CO[i-1]);
           end
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $lcu``.
