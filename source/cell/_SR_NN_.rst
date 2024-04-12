$_SR_NN_
========

A set-reset latch with negative polarity SET and negative polarity RESET.
::

   Truth table:    S R | Q
                  -----+---
                   - 0 | 0
                   0 - | 1
                   - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:476

   module \$_SR_NN_ (S, R, Q);
       input S, R;
       output reg Q;
       always @* begin
           if (R == 0)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SR_NN_``.
