$_DLATCH_PN0_
=============

A positive enable D-type latch with negative polarity reset.
::

   Truth table:    E R D | Q
                  -------+---
                   - 0 - | 0
                   1 - d | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3315

   module \$_DLATCH_PN0_ (E, R, D, Q);
       input E, R, D;
       output reg Q;
       always @* begin
           if (R == 0)
                       Q <= 0;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_PN0_``.
