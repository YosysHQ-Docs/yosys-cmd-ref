$_ALDFFE_PPN_
=============

.. cell:def:: $_ALDFFE_PPN_
   :title: $_ALDFFE_PPN_

   A positive edge D-type flip-flop with positive polarity async load and negative
   polarity clock enable.
   ::
   
      Truth table:    D C L AD E | Q
                     ------------+---
                      - - 1 a  - | a
                      d / - -  0 | d
                      - - - -  - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1504

   module \$_ALDFFE_PPN_ (D, C, L, AD, E, Q);
       input D, C, L, AD, E;
       output reg Q;
       always @(posedge C or posedge L) begin
           if (L == 1)
               Q <= AD;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFFE_PPN_``.
