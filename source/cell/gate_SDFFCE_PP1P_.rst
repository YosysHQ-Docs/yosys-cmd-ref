$_SDFFCE_PP1P_
==============

.. cell:def:: $_SDFFCE_PP1P_
   :title: $_SDFFCE_PP1P_

   A positive edge D-type flip-flop with positive polarity synchronous set and positive
   polarity clock enable (with clock enable having priority).
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - / 1 1 | 1
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
   :caption: simcells.v:3158

   module \$_SDFFCE_PP1P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C) begin
           if (E == 1) begin
               if (R == 1)
                   Q <= 1;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_PP1P_``.
