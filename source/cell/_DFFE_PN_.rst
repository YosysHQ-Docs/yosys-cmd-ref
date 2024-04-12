$_DFFE_PN_
==========

A positive edge D-type flip-flop with negative polarity enable.
::

   Truth table:    D C E | Q
                  -------+---
                   d / 0 | d
                   - - - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:660

   module \$_DFFE_PN_ (D, C, E, Q);
       input D, C, E;
       output reg Q;
       always @(posedge C) begin
           if (!E) Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_PN_``.
