$_OAI3_
=======

.. cell:def:: $_OAI3_
   :title: $_OAI3_

   A 3-input Or-And-Invert gate.
   ::
   
      Truth table:    A B C | Y
                     -------+---
                      0 0 0 | 1
                      0 0 1 | 1
                      0 1 0 | 1
                      0 1 1 | 0
                      1 0 0 | 1
                      1 0 1 | 0
                      1 1 0 | 1
                      1 1 1 | 0
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:374

   module \$_OAI3_ (A, B, C, Y);
       input A, B, C;
       output Y;
       assign Y = ~((A | B) & C);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_OAI3_``.
