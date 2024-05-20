$_ANDNOT_
=========

.. cell:def:: $_ANDNOT_
   :title: $_ANDNOT_

   A 2-input AND-NOT gate.
   ::
   
      Truth table:    A B | Y
                     -----+---
                      0 0 | 0
                      0 1 | 0
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
   :caption: simcells.v:189

   module \$_ANDNOT_ (A, B, Y);
       input A, B;
       output Y;
       assign Y = A & (~B);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ANDNOT_``.
