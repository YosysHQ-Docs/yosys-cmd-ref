$_SDFF_PN0_
===========

.. cell:def:: $_SDFF_PN0_
   :title: $_SDFF_PN0_

   A positive edge D-type flip-flop with negative polarity synchronous reset.
   ::
   
      Truth table:    D C R | Q
                     -------+---
                      - / 0 | 0
                      d / - | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2291

   module \$_SDFF_PN0_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(posedge C) begin
           if (R == 0)
               Q <= 0;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFF_PN0_``.
