$_SDFFCE_NN0P_
==============

.. cell:def:: $_SDFFCE_NN0P_
   :title: $_SDFFCE_NN0P_

   A negative edge D-type flip-flop with negative polarity synchronous reset and positive
   polarity clock enable (with clock enable having priority).
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - \ 0 1 | 0
                      d \ - 1 | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2794

   module \$_SDFFCE_NN0P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C) begin
           if (E == 1) begin
               if (R == 0)
                   Q <= 0;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_NN0P_``.
