$_SDFFCE_NN0N_
==============

.. cell:def:: $_SDFFCE_NN0N_
   :title: $_SDFFCE_NN0N_

   A negative edge D-type flip-flop with negative polarity synchronous reset and negative
   polarity clock enable (with clock enable having priority).
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - \ 0 0 | 0
                      d \ - 0 | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2768

   module \$_SDFFCE_NN0N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C) begin
           if (E == 0) begin
               if (R == 0)
                   Q <= 0;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_NN0N_``.
