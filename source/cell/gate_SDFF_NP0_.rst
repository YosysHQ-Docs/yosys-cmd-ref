$_SDFF_NP0_
===========

.. cell:def:: $_SDFF_NP0_
   :title: $_SDFF_NP0_

   A negative edge D-type flip-flop with positive polarity synchronous reset.
   ::
   
      Truth table:    D C R | Q
                     -------+---
                      - \ 1 | 0
                      d \ - | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2245

   module \$_SDFF_NP0_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(negedge C) begin
           if (R == 1)
               Q <= 0;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFF_NP0_``.
