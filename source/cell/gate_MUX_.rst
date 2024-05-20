$_MUX_
======

.. cell:def:: $_MUX_
   :title: $_MUX_

   A 2-input MUX gate.
   ::
   
      Truth table:    A B S | Y
                     -------+---
                      a - 0 | a
                      - b 1 | b
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:225

   module \$_MUX_ (A, B, S, Y);
       input A, B, S;
       output Y;
       assign Y = S ? B : A;
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_MUX_``.
