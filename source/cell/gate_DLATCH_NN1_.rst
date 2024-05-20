$_DLATCH_NN1_
=============

.. cell:def:: $_DLATCH_NN1_
   :title: $_DLATCH_NN1_

   A negative enable D-type latch with negative polarity set.
   ::
   
      Truth table:    E R D | Q
                     -------+---
                      - 0 - | 1
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
   :caption: simcells.v:3246

   module \$_DLATCH_NN1_ (E, R, D, Q);
       input E, R, D;
       output reg Q;
       always @* begin
           if (R == 0)
                       Q <= 1;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_NN1_``.
