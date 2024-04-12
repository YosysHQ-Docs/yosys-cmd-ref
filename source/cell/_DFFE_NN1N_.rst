$_DFFE_NN1N_
============

A negative edge D-type flip-flop with negative polarity set and negative
polarity clock enable.
::

   Truth table:    D C R E | Q
                  ---------+---
                   - - 0 - | 1
                   d \ - 0 | d
                   - - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:932

   module \$_DFFE_NN1N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C or negedge R) begin
           if (R == 0)
               Q <= 1;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_NN1N_``.
