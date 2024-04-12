$check
======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1868

   module \$check (A, EN, TRG, ARGS);
       
       parameter FLAVOR = "";
       parameter PRIORITY = 0;
       
       parameter FORMAT = "";
       parameter ARGS_WIDTH = 0;
       
       parameter TRG_ENABLE = 1;
       parameter TRG_WIDTH = 0;
       parameter TRG_POLARITY = 0;
       
       input A;
       input EN;
       input [TRG_WIDTH-1:0] TRG;
       input [ARGS_WIDTH-1:0] ARGS;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $check``.
