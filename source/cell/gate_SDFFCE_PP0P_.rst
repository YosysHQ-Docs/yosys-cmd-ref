$_SDFFCE_PP0P_
==============

.. cell:def:: $_SDFFCE_PP0P_
   :title: $_SDFFCE_PP0P_

   A positive edge D-type flip-flop with positive polarity synchronous reset and positive
   polarity clock enable (with clock enable having priority).
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - / 1 1 | 0
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
   :caption: simcells.v:3106

   module \$_SDFFCE_PP0P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C) begin
           if (E == 1) begin
               if (R == 1)
                   Q <= 0;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_PP0P_``.
