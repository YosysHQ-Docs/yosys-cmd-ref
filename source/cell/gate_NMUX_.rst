$_NMUX_
=======

.. cell:def:: $_NMUX_
   :title: $_NMUX_

   A 2-input inverting MUX gate.
   ::
   
      Truth table:    A B S | Y
                     -------+---
                      0 - 0 | 1
                      1 - 0 | 0
                      - 0 1 | 1
                      - 1 1 | 0
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:244

   module \$_NMUX_ (A, B, S, Y);
       input A, B, S;
       output Y;
       assign Y = S ? !B : !A;
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_NMUX_``.
