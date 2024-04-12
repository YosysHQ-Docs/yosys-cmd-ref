$_TBUF_
=======

A tri-state buffer.
::

   Truth table:    A E | Y
                  -----+---
                   a 1 | a
                   - 0 | z
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:453

   module \$_TBUF_ (A, E, Y);
       input A, E;
       output Y;
       assign Y = E ? A : 1'bz;
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_TBUF_``.
