$_XNOR_
=======

.. cell:def:: $_XNOR_
   :title: $_XNOR_

   A 2-input XNOR gate.
   ::
   
      Truth table:    A B | Y
                     -----+---
                      0 0 | 1
                      0 1 | 0
                      1 0 | 0
                      1 1 | 1
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:170

   module \$_XNOR_ (A, B, Y);
       input A, B;
       output Y;
       assign Y = ~(A ^ B);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_XNOR_``.
