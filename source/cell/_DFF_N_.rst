$_DFF_N_
========

A negative edge D-type flip-flop.
::

   Truth table:    D C | Q
                  -----+---
                   d \ | d
                   - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:584

   module \$_DFF_N_ (D, C, Q);
       input D, C;
       output reg Q;
       always @(negedge C) begin
           Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_N_``.
