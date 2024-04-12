$_DFFSR_PNN_
============

A positive edge D-type flip-flop with negative polarity set and negative
polarity reset.
::

   Truth table:    C S R D | Q
                  ---------+---
                   - - 0 - | 0
                   - 0 - - | 1
                   / - - d | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1661

   module \$_DFFSR_PNN_ (C, S, R, D, Q);
       input C, S, R, D;
       output reg Q;
       always @(posedge C, negedge S, negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSR_PNN_``.
