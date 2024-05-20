$_ORNOT_
========

.. cell:def:: $_ORNOT_
   :title: $_ORNOT_

   A 2-input OR-NOT gate.
   ::
   
      Truth table:    A B | Y
                     -----+---
                      0 0 | 1
                      0 1 | 0
                      1 0 | 1
                      1 1 | 1
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:208

   module \$_ORNOT_ (A, B, Y);
       input A, B;
       output Y;
       assign Y = A | (~B);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ORNOT_``.
