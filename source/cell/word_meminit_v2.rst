$meminit_v2
===========

.. cell:def:: $meminit_v2
   :title: $meminit_v2

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2511

   module \$meminit_v2 (ADDR, DATA, EN);
       
       parameter MEMID = "";
       parameter ABITS = 8;
       parameter WIDTH = 8;
       parameter WORDS = 1;
       
       parameter PRIORITY = 0;
       
       input [ABITS-1:0] ADDR;
       input [WORDS*WIDTH-1:0] DATA;
       input [WIDTH-1:0] EN;
       
       initial begin
           if (MEMID != "") begin
               $display("ERROR: Found non-simulatable instance of $meminit_v2!");
               $finish;
           end
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $meminit_v2``.
