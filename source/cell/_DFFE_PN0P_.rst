$_DFFE_PN0P_
============

A positive edge D-type flip-flop with negative polarity reset and positive
polarity clock enable.
::

   Truth table:    D C R E | Q
                  ---------+---
                   - - 0 - | 0
                   d / - 1 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1100

   module \$_DFFE_PN0P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C or negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_PN0P_``.
