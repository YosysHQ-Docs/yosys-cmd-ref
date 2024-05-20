$_DFFSRE_NNNN_
==============

.. cell:def:: $_DFFSRE_NNNN_
   :title: $_DFFSRE_NNNN_

   A negative edge D-type flip-flop with negative polarity set, negative
   polarity reset and negative polarity clock enable.
   ::
   
      Truth table:    C S R E D | Q
                     -----------+---
                      - - 0 - - | 0
                      - 0 - - - | 1
                      \ - - 0 d | d
                      - - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1769

   module \$_DFFSRE_NNNN_ (C, S, R, E, D, Q);
       input C, S, R, E, D;
       output reg Q;
       always @(negedge C, negedge S, negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
               else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSRE_NNNN_``.
