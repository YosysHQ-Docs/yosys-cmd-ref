$_DFFSRE_PPNN_
==============

.. cell:def:: $_DFFSRE_PPNN_
   :title: $_DFFSRE_PPNN_

   A positive edge D-type flip-flop with positive polarity set, negative
   polarity reset and negative polarity clock enable.
   ::
   
      Truth table:    C S R E D | Q
                     -----------+---
                      - - 0 - - | 0
                      - 1 - - - | 1
                      / - - 0 d | d
                      - - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2093

   module \$_DFFSRE_PPNN_ (C, S, R, E, D, Q);
       input C, S, R, E, D;
       output reg Q;
       always @(posedge C, posedge S, negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
               else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSRE_PPNN_``.
