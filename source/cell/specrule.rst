$specrule
=========

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1620

   module \$specrule (EN_SRC, EN_DST, SRC, DST);
       
       parameter TYPE = "";
       parameter T_LIMIT = 0;
       parameter T_LIMIT2 = 0;
       
       parameter SRC_WIDTH = 1;
       parameter DST_WIDTH = 1;
       
       parameter SRC_PEN = 0;
       parameter SRC_POL = 0;
       
       parameter DST_PEN = 0;
       parameter DST_POL = 0;
       
       input EN_SRC, EN_DST;
       input [SRC_WIDTH-1:0] SRC;
       input [DST_WIDTH-1:0] DST;
       
       `ifdef SIMLIB_SPECIFY
       specify
           // TBD
       endspecify
       `endif
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $specrule``.
