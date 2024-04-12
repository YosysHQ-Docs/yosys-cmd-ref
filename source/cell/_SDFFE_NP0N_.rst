$_SDFFE_NP0N_
=============

A negative edge D-type flip-flop with positive polarity synchronous reset and negative
polarity clock enable (with reset having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - \ 1 - | 0
                   d \ - 0 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2480

   module \$_SDFFE_NP0N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C) begin
           if (R == 1)
               Q <= 0;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFE_NP0N_``.
