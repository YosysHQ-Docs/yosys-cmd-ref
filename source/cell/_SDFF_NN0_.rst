$_SDFF_NN0_
===========

A negative edge D-type flip-flop with negative polarity synchronous reset.
::

   Truth table:    D C R | Q
                  -------+---
                   - \ 0 | 0
                   d \ - | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2199

   module \$_SDFF_NN0_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(negedge C) begin
           if (R == 0)
               Q <= 0;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFF_NN0_``.
