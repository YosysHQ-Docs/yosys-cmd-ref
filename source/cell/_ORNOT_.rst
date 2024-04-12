$_ORNOT_
========

A 2-input OR-NOT gate.
::

   Truth table:    A B | Y
                  -----+---
                   0 0 | 1
                   0 1 | 0
                   1 0 | 1
                   1 1 | 1
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:208

   module \$_ORNOT_ (A, B, Y);
       input A, B;
       output Y;
       assign Y = A | (~B);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ORNOT_``.
