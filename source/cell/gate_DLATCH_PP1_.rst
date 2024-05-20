$_DLATCH_PP1_
=============

.. cell:def:: $_DLATCH_PP1_
   :title: $_DLATCH_PP1_

   A positive enable D-type latch with positive polarity set.
   ::
   
      Truth table:    E R D | Q
                     -------+---
                      - 1 - | 1
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
   :caption: simcells.v:3384

   module \$_DLATCH_PP1_ (E, R, D, Q);
       input E, R, D;
       output reg Q;
       always @* begin
           if (R == 1)
                       Q <= 1;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_PP1_``.
