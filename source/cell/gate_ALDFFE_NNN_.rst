$_ALDFFE_NNN_
=============

.. cell:def:: $_ALDFFE_NNN_
   :title: $_ALDFFE_NNN_

   A negative edge D-type flip-flop with negative polarity async load and negative
   polarity clock enable.
   ::
   
      Truth table:    D C L AD E | Q
                     ------------+---
                      - - 0 a  - | a
                      d \ - -  0 | d
                      - - - -  - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1360

   module \$_ALDFFE_NNN_ (D, C, L, AD, E, Q);
       input D, C, L, AD, E;
       output reg Q;
       always @(negedge C or negedge L) begin
           if (L == 0)
               Q <= AD;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFFE_NNN_``.
