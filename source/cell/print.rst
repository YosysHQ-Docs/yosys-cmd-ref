$print
======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1849

   module \$print (EN, TRG, ARGS);
       
       parameter PRIORITY = 0;
       
       parameter FORMAT = "";
       parameter ARGS_WIDTH = 0;
       
       parameter TRG_ENABLE = 1;
       parameter TRG_WIDTH = 0;
       parameter TRG_POLARITY = 0;
       
       input EN;
       input [TRG_WIDTH-1:0] TRG;
       input [ARGS_WIDTH-1:0] ARGS;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $print``.
