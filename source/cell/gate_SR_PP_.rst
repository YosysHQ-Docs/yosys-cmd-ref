$_SR_PP_
========

.. cell:def:: $_SR_PP_
   :title: $_SR_PP_

   A set-reset latch with positive polarity SET and positive polarity RESET.
   ::
   
      Truth table:    S R | Q
                     -----+---
                      - 1 | 0
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
   :caption: simcells.v:545

   module \$_SR_PP_ (S, R, Q);
       input S, R;
       output reg Q;
       always @* begin
           if (R == 1)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SR_PP_``.
