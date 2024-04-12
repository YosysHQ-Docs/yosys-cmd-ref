$_SDFF_PN1_
===========

A positive edge D-type flip-flop with negative polarity synchronous set.
::

   Truth table:    D C R | Q
                  -------+---
                   - / 0 | 1
                   d / - | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:2314

   module \$_SDFF_PN1_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(posedge C) begin
           if (R == 0)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_SDFF_PN1_``.
