$_OAI4_
=======

A 4-input Or-And-Invert gate.
::

   Truth table:    A B C D | Y
                  ---------+---
                   0 0 0 0 | 1
                   0 0 0 1 | 1
                   0 0 1 0 | 1
                   0 0 1 1 | 1
                   0 1 0 0 | 1
                   0 1 0 1 | 0
                   0 1 1 0 | 0
                   0 1 1 1 | 0
                   1 0 0 0 | 1
                   1 0 0 1 | 0
                   1 0 1 0 | 0
                   1 0 1 1 | 0
                   1 1 0 0 | 1
                   1 1 0 1 | 0
                   1 1 1 0 | 0
                   1 1 1 1 | 0
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:436

   module \$_OAI4_ (A, B, C, D, Y);
       input A, B, C, D;
       output Y;
       assign Y = ~((A | B) & (C | D));
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_OAI4_``.
