$_DFFSRE_PNNP_
==============

A positive edge D-type flip-flop with negative polarity set, negative
polarity reset and positive polarity clock enable.
::

   Truth table:    C S R E D | Q
                  -----------+---
                   - - 0 - - | 0
                   - 0 - - - | 1
                   / - - 1 d | d
                   - - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2012

   module \$_DFFSRE_PNNP_ (C, S, R, E, D, Q);
       input C, S, R, E, D;
       output reg Q;
       always @(posedge C, negedge S, negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
               else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSRE_PNNP_``.
