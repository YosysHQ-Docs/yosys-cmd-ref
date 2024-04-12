$_SDFF_PP0_
===========

A positive edge D-type flip-flop with positive polarity synchronous reset.
::

   Truth table:    D C R | Q
                  -------+---
                   - / 1 | 0
                   d / - | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2337

   module \$_SDFF_PP0_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(posedge C) begin
           if (R == 1)
               Q <= 0;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFF_PP0_``.
