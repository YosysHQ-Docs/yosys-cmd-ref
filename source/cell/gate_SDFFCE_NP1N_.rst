$_SDFFCE_NP1N_
==============

.. cell:def:: $_SDFFCE_NP1N_
   :title: $_SDFFCE_NP1N_

   A negative edge D-type flip-flop with positive polarity synchronous set and negative
   polarity clock enable (with clock enable having priority).
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - \ 1 0 | 1
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
   :caption: simcells.v:2924

   module \$_SDFFCE_NP1N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C) begin
           if (E == 0) begin
               if (R == 1)
                   Q <= 1;
               else
                   Q <= D;
           end
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFFCE_NP1N_``.
