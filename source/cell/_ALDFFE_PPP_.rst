$_ALDFFE_PPP_
=============

A positive edge D-type flip-flop with positive polarity async load and positive
polarity clock enable.
::

   Truth table:    D C L AD E | Q
                  ------------+---
                   - - 1 a  - | a
                   d / - -  1 | d
                   - - - -  - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1528

   module \$_ALDFFE_PPP_ (D, C, L, AD, E, Q);
       input D, C, L, AD, E;
       output reg Q;
       always @(posedge C or posedge L) begin
           if (L == 1)
               Q <= AD;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFFE_PPP_``.
