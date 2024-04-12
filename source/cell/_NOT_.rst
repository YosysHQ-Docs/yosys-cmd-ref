$_NOT_
======

An inverter gate.
::

   Truth table:    A | Y
                  ---+---
                   0 | 1
                   1 | 0
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:56

   module \$_NOT_ (A, Y);
       input A;
       output Y;
       assign Y = ~A;
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_NOT_``.
