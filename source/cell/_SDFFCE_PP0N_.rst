$_SDFFCE_PP0N_
==============

A positive edge D-type flip-flop with positive polarity synchronous reset and negative
polarity clock enable (with clock enable having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - / 1 0 | 0
                   d / - 0 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3080

   module \$_SDFFCE_PP0N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C) begin
           if (E == 0) begin
               if (R == 1)
                   Q <= 0;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_PP0N_``.
