$_SDFFE_NP0P_
=============

A negative edge D-type flip-flop with positive polarity synchronous reset and positive
polarity clock enable (with reset having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - \ 1 - | 0
                   d \ - 1 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2504

   module \$_SDFFE_NP0P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C) begin
           if (R == 1)
               Q <= 0;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFE_NP0P_``.
