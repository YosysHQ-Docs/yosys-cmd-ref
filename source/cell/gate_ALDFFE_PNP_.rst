$_ALDFFE_PNP_
=============

.. cell:def:: $_ALDFFE_PNP_
   :title: $_ALDFFE_PNP_

   A positive edge D-type flip-flop with negative polarity async load and positive
   polarity clock enable.
   ::
   
      Truth table:    D C L AD E | Q
                     ------------+---
                      - - 0 a  - | a
                      d / - -  1 | d
                      - - - -  - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

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
