$_DLATCHSR_PNN_
===============

.. cell:def:: $_DLATCHSR_PNN_
   :title: $_DLATCHSR_PNN_

   A positive enable D-type latch with negative polarity set and negative
   polarity reset.
   ::
   
      Truth table:    E S R D | Q
                     ---------+---
                      - - 0 - | 0
                      - 0 - - | 1
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
   :caption: simcells.v:3517

   module \$_DLATCHSR_PNN_ (E, S, R, D, Q);
       input E, S, R, D;
       output reg Q;
       always @* begin
           if (R == 0)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCHSR_PNN_``.
