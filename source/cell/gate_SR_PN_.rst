$_SR_PN_
========

.. cell:def:: $_SR_PN_
   :title: $_SR_PN_

   A set-reset latch with positive polarity SET and negative polarity RESET.
   ::
   
      Truth table:    S R | Q
                     -----+---
                      - 0 | 0
                      1 - | 1
                      - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:522

   module \$_SR_PN_ (S, R, Q);
       input S, R;
       output reg Q;
       always @* begin
           if (R == 0)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SR_PN_``.
