$_DFFSRE_PPPP_
==============

.. cell:def:: $_DFFSRE_PPPP_
   :title: $_DFFSRE_PPPP_

   A positive edge D-type flip-flop with positive polarity set, positive
   polarity reset and positive polarity clock enable.
   ::
   
      Truth table:    C S R E D | Q
                     -----------+---
                      - - 1 - - | 0
                      - 1 - - - | 1
                      / - - 1 d | d
                      - - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2174

   module \$_DFFSRE_PPPP_ (C, S, R, E, D, Q);
       input C, S, R, E, D;
       output reg Q;
       always @(posedge C, posedge S, posedge R) begin
           if (R == 1)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
               else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSRE_PPPP_``.
