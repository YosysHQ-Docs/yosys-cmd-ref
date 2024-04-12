$_ALDFFE_NPN_
=============

A negative edge D-type flip-flop with positive polarity async load and negative
polarity clock enable.
::

   Truth table:    D C L AD E | Q
                  ------------+---
                   - - 1 a  - | a
                   d \ - -  0 | d
                   - - - -  - | q
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1408

   module \$_ALDFFE_NPN_ (D, C, L, AD, E, Q);
       input D, C, L, AD, E;
       output reg Q;
       always @(negedge C or posedge L) begin
           if (L == 1)
               Q <= AD;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFFE_NPN_``.
