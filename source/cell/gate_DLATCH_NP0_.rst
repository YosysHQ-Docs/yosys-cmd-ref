$_DLATCH_NP0_
=============

.. cell:def:: $_DLATCH_NP0_
   :title: $_DLATCH_NP0_

   A negative enable D-type latch with positive polarity reset.
   ::
   
      Truth table:    E R D | Q
                     -------+---
                      - 1 - | 0
                      0 - d | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3269

   module \$_DLATCH_NP0_ (E, R, D, Q);
       input E, R, D;
       output reg Q;
       always @* begin
           if (R == 1)
                       Q <= 0;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_NP0_``.
