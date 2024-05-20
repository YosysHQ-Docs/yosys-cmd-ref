$_SR_NP_
========

.. cell:def:: $_SR_NP_
   :title: $_SR_NP_

   A set-reset latch with negative polarity SET and positive polarity RESET.
   ::
   
      Truth table:    S R | Q
                     -----+---
                      - 1 | 0
                      0 - | 1
                      - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:499

   module \$_SR_NP_ (S, R, Q);
       input S, R;
       output reg Q;
       always @* begin
           if (R == 1)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SR_NP_``.
