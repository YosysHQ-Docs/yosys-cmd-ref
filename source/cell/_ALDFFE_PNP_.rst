$_ALDFFE_PNP_
=============

A positive edge D-type flip-flop with negative polarity async load and positive
polarity clock enable.
::

   Truth table:    D C L AD E | Q
                  ------------+---
                   - - 0 a  - | a
                   d / - -  1 | d
                   - - - -  - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1480

   module \$_ALDFFE_PNP_ (D, C, L, AD, E, Q);
       input D, C, L, AD, E;
       output reg Q;
       always @(posedge C or negedge L) begin
           if (L == 0)
               Q <= AD;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFFE_PNP_``.
