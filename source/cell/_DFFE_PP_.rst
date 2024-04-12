$_DFFE_PP_
==========

A positive edge D-type flip-flop with positive polarity enable.
::

   Truth table:    D C E | Q
                  -------+---
                   d / 1 | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:679

   module \$_DFFE_PP_ (D, C, E, Q);
       input D, C, E;
       output reg Q;
       always @(posedge C) begin
           if (E) Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_PP_``.
