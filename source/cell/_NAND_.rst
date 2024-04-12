$_NAND_
=======

A 2-input NAND gate.
::

   Truth table:    A B | Y
                  -----+---
                   0 0 | 1
                   0 1 | 1
                   1 0 | 1
                   1 1 | 0
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:94

   module \$_NAND_ (A, B, Y);
       input A, B;
       output Y;
       assign Y = ~(A & B);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_NAND_``.
