$_SDFFE_PP1N_
=============

A positive edge D-type flip-flop with positive polarity synchronous set and negative
polarity clock enable (with set having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - / 1 - | 1
                   d / - 0 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2720

   module \$_SDFFE_PP1N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C) begin
           if (R == 1)
               Q <= 1;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFE_PP1N_``.
