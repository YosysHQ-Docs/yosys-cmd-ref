$_MUX8_
=======

An 8-input MUX gate.
::

   Truth table:    A B C D E F G H S T U | Y
                  -----------------------+---
                   a - - - - - - - 0 0 0 | a
                   - b - - - - - - 1 0 0 | b
                   - - c - - - - - 0 1 0 | c
                   - - - d - - - - 1 1 0 | d
                   - - - - e - - - 0 0 1 | e
                   - - - - - f - - 1 0 1 | f
                   - - - - - - g - 0 1 1 | g
                   - - - - - - - h 1 1 1 | h
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:287

   module \$_MUX8_ (A, B, C, D, E, F, G, H, S, T, U, Y);
       input A, B, C, D, E, F, G, H, S, T, U;
       output Y;
       assign Y = U ? T ? (S ? H : G) :
                          (S ? F : E) :
                      T ? (S ? D : C) :
                          (S ? B : A);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_MUX8_``.
