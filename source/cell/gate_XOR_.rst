$_XOR_
======

.. cell:def:: $_XOR_
   :title: $_XOR_

   A 2-input XOR gate.
   ::
   
      Truth table:    A B | Y
                     -----+---
                      0 0 | 0
                      0 1 | 1
                      1 0 | 1
                      1 1 | 0
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:151

   module \$_XOR_ (A, B, Y);
       input A, B;
       output Y;
       assign Y = A ^ B;
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_XOR_``.
