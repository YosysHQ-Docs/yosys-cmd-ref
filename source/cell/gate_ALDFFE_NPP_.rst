$_ALDFFE_NPP_
=============

.. cell:def:: $_ALDFFE_NPP_
   :title: $_ALDFFE_NPP_

   A negative edge D-type flip-flop with positive polarity async load and positive
   polarity clock enable.
   ::
   
      Truth table:    D C L AD E | Q
                     ------------+---
                      - - 1 a  - | a
                      d \ - -  1 | d
                      - - - -  - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1432

   module \$_ALDFFE_NPP_ (D, C, L, AD, E, Q);
       input D, C, L, AD, E;
       output reg Q;
       always @(negedge C or posedge L) begin
           if (L == 1)
               Q <= AD;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFFE_NPP_``.
