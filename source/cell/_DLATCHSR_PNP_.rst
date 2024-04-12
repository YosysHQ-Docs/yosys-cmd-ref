$_DLATCHSR_PNP_
===============

A positive enable D-type latch with negative polarity set and positive
polarity reset.
::

   Truth table:    E S R D | Q
                  ---------+---
                   - - 1 - | 0
                   - 0 - - | 1
                   1 - - d | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3544

   module \$_DLATCHSR_PNP_ (E, S, R, D, Q);
       input E, S, R, D;
       output reg Q;
       always @* begin
           if (R == 1)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCHSR_PNP_``.
