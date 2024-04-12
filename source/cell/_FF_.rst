$_FF_
=====

A D-type flip-flop that is clocked from the implicit global clock. (This cell
type is usually only used in netlists for formal verification.)

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:564

   module \$_FF_ (D, Q);
       input D;
       output reg Q;
       always @($global_clock) begin
           Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_FF_``.
