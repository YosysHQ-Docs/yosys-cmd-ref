$_DFF_PN0_
==========

A positive edge D-type flip-flop with negative polarity reset.
::

   Truth table:    D C R | Q
                  -------+---
                   - - 0 | 0
                   d / - | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:791

   module \$_DFF_PN0_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(posedge C or negedge R) begin
           if (R == 0)
               Q <= 0;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_PN0_``.
