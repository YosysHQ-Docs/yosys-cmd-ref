$tribuf
=======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1460

   module \$tribuf (A, EN, Y);
       
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] A;
       input EN;
       output [WIDTH-1:0] Y;
       
       assign Y = EN ? A : 'bz;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $tribuf``.
