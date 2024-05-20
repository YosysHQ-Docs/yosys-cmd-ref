$_DLATCHSR_PPN_
===============

.. cell:def:: $_DLATCHSR_PPN_
   :title: $_DLATCHSR_PPN_

   A positive enable D-type latch with positive polarity set and negative
   polarity reset.
   ::
   
      Truth table:    E S R D | Q
                     ---------+---
                      - - 0 - | 0
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
   :caption: simcells.v:3571

   module \$_DLATCHSR_PPN_ (E, S, R, D, Q);
       input E, S, R, D;
       output reg Q;
       always @* begin
           if (R == 0)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCHSR_PPN_``.
