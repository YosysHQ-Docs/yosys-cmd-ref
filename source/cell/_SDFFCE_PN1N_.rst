$_SDFFCE_PN1N_
==============

A positive edge D-type flip-flop with negative polarity synchronous set and negative
polarity clock enable (with clock enable having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - / 0 0 | 1
                   d / - 0 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3028

   module \$_SDFFCE_PN1N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C) begin
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
   ``help $_SDFFCE_PN1N_``.
