$_DLATCH_PP0_
=============

.. cell:def:: $_DLATCH_PP0_
   :title: $_DLATCH_PP0_

   A positive enable D-type latch with positive polarity reset.
   ::
   
      Truth table:    E R D | Q
                     -------+---
                      - 1 - | 0
                      1 - d | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3361

   module \$_DLATCH_PP0_ (E, R, D, Q);
       input E, R, D;
       output reg Q;
       always @* begin
           if (R == 1)
                       Q <= 0;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_PP0_``.
