$memrd_v2
=========

.. cell:def:: $memrd_v2
   :title: $memrd_v2

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2407

   module \$memrd_v2 (CLK, EN, ARST, SRST, ADDR, DATA);
       
       parameter MEMID = "";
       parameter ABITS = 8;
       parameter WIDTH = 8;
       
       parameter CLK_ENABLE = 0;
       parameter CLK_POLARITY = 0;
       parameter TRANSPARENCY_MASK = 0;
       parameter COLLISION_X_MASK = 0;
       parameter ARST_VALUE = 0;
       parameter SRST_VALUE = 0;
       parameter INIT_VALUE = 0;
       parameter CE_OVER_SRST = 0;
       
       input CLK, EN, ARST, SRST;
       input [ABITS-1:0] ADDR;
       output [WIDTH-1:0] DATA;
       
       initial begin
           if (MEMID != "") begin
               $display("ERROR: Found non-simulatable instance of $memrd_v2!");
               $finish;
           end
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $memrd_v2``.
