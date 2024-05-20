$_BUF_
======

.. cell:def:: $_BUF_
   :title: $_BUF_

   A buffer. This cell type is always optimized away by the opt_clean pass.
   ::
   
      Truth table:    A | Y
                     ---+---
                      0 | 0
                      1 | 1
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:39

   module \$_BUF_ (A, Y);
       input A;
       output Y;
       assign Y = A;
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_BUF_``.
