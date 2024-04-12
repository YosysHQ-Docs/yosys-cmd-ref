$_DLATCH_N_
===========

A negative enable D-type latch.
::

   Truth table:    E D | Q
                  -----+---
                   0 d | d
                   - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:3182

   module \$_DLATCH_N_ (E, D, Q);
       input E, D;
       output reg Q;
       always @* begin
           if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DLATCH_N_``.
