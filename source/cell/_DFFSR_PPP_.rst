$_DFFSR_PPP_
============

A positive edge D-type flip-flop with positive polarity set and positive
polarity reset.
::

   Truth table:    C S R D | Q
                  ---------+---
                   - - 1 - | 0
                   - 1 - - | 1
                   / - - d | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1742

   module \$_DFFSR_PPP_ (C, S, R, D, Q);
       input C, S, R, D;
       output reg Q;
       always @(posedge C, posedge S, posedge R) begin
           if (R == 1)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSR_PPP_``.
