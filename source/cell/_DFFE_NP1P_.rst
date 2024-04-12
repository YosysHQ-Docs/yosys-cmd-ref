$_DFFE_NP1P_
============

A negative edge D-type flip-flop with positive polarity set and positive
polarity clock enable.
::

   Truth table:    D C R E | Q
                  ---------+---
                   - - 1 - | 1
                   d \ - 1 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1052

   module \$_DFFE_NP1P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C or posedge R) begin
           if (R == 1)
               Q <= 1;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_NP1P_``.
