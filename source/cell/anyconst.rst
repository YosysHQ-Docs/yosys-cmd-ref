$anyconst
=========

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1761

   module \$anyconst (Y);
       
       parameter WIDTH = 0;
       
       output [WIDTH-1:0] Y;
       
       assign Y = 'bx;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $anyconst``.
