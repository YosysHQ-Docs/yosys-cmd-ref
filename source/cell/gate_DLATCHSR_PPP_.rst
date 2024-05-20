$_DLATCHSR_PPP_
===============

.. cell:def:: $_DLATCHSR_PPP_
   :title: $_DLATCHSR_PPP_

   A positive enable D-type latch with positive polarity set and positive
   polarity reset.
   ::
   
      Truth table:    E S R D | Q
                     ---------+---
                      - - 1 - | 0
                      - 1 - - | 1
                      1 - - d | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3598

   module \$_DLATCHSR_PPP_ (E, S, R, D, Q);
       input E, S, R, D;
       output reg Q;
       always @* begin
           if (R == 1)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCHSR_PPP_``.
