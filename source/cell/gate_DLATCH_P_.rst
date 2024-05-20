$_DLATCH_P_
===========

.. cell:def:: $_DLATCH_P_
   :title: $_DLATCH_P_

   A positive enable D-type latch.
   ::
   
      Truth table:    E D | Q
                     -----+---
                      1 d | d
                      - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3202

   module \$_DLATCH_P_ (E, D, Q);
       input E, D;
       output reg Q;
       always @* begin
           if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_P_``.
