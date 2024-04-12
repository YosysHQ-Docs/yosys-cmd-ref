$memwr_v2
=========

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2461

   module \$memwr_v2 (CLK, EN, ADDR, DATA);
       
       parameter MEMID = "";
       parameter ABITS = 8;
       parameter WIDTH = 8;
       
       parameter CLK_ENABLE = 0;
       parameter CLK_POLARITY = 0;
       parameter PORTID = 0;
       parameter PRIORITY_MASK = 0;
       
       input CLK;
       input [WIDTH-1:0] EN;
       input [ABITS-1:0] ADDR;
       input [WIDTH-1:0] DATA;
       
       initial begin
           if (MEMID != "") begin
               $display("ERROR: Found non-simulatable instance of $memwr_v2!");
               $finish;
           end
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $memwr_v2``.
