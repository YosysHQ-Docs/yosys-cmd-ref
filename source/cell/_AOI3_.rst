$_AOI3_
=======

A 3-input And-Or-Invert gate.
::

   Truth table:    A B C | Y
                  -------+---
                   0 0 0 | 1
                   0 0 1 | 0
                   0 1 0 | 1
                   0 1 1 | 0
                   1 0 0 | 1
                   1 0 1 | 0
                   1 1 0 | 0
                   1 1 1 | 0
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:351

   module \$_AOI3_ (A, B, C, Y);
       input A, B, C;
       output Y;
       assign Y = ~((A & B) | C);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_AOI3_``.
