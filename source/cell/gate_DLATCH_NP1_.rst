$_DLATCH_NP1_
=============

.. cell:def:: $_DLATCH_NP1_
   :title: $_DLATCH_NP1_

   A negative enable D-type latch with positive polarity set.
   ::
   
      Truth table:    E R D | Q
                     -------+---
                      - 1 - | 1
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
   :caption: simcells.v:3292

   module \$_DLATCH_NP1_ (E, R, D, Q);
       input E, R, D;
       output reg Q;
       always @* begin
           if (R == 1)
                       Q <= 1;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_NP1_``.
