$_DFF_P_
========

A positive edge D-type flip-flop.
::

   Truth table:    D C | Q
                  -----+---
                   d / | d
                   - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:603

   module \$_DFF_P_ (D, C, Q);
       input D, C;
       output reg Q;
       always @(posedge C) begin
           Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_P_``.
