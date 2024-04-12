$_SDFFCE_NP1P_
==============

A negative edge D-type flip-flop with positive polarity synchronous set and positive
polarity clock enable (with clock enable having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - \ 1 1 | 1
                   d \ - 1 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2950

   module \$_SDFFCE_NP1P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C) begin
           if (E == 1) begin
               if (R == 1)
                   Q <= 1;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_NP1P_``.
