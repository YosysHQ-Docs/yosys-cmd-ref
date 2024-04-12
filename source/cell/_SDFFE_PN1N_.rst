$_SDFFE_PN1N_
=============

A positive edge D-type flip-flop with negative polarity synchronous set and negative
polarity clock enable (with set having priority).
::

   Truth table:    D C R E | Q
                  ---------+---
                   - / 0 - | 1
                   d / - 0 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2624

   module \$_SDFFE_PN1N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C) begin
           if (R == 0)
               Q <= 1;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFE_PN1N_``.
