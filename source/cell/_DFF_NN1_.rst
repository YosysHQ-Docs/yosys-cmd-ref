$_DFF_NN1_
==========

A negative edge D-type flip-flop with negative polarity set.
::

   Truth table:    D C R | Q
                  -------+---
                   - - 0 | 1
                   d \ - | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:722

   module \$_DFF_NN1_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(negedge C or negedge R) begin
           if (R == 0)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_NN1_``.
