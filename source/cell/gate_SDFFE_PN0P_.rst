$_SDFFE_PN0P_
=============

.. cell:def:: $_SDFFE_PN0P_
   :title: $_SDFFE_PN0P_

   A positive edge D-type flip-flop with negative polarity synchronous reset and positive
   polarity clock enable (with reset having priority).
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - / 0 - | 0
                      d / - 1 | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2600

   module \$_SDFFE_PN0P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C) begin
           if (R == 0)
               Q <= 0;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFE_PN0P_``.
