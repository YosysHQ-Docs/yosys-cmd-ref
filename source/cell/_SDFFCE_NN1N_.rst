$_SDFFCE_NN1N_
==============

A negative edge D-type flip-flop with negative polarity synchronous set and negative
polarity clock enable (with clock enable having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - \ 0 0 | 1
                   d \ - 0 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2820

   module \$_SDFFCE_NN1N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C) begin
           if (E == 0) begin
               if (R == 0)
                   Q <= 1;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_NN1N_``.
