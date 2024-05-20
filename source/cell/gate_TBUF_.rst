$_TBUF_
=======

.. cell:def:: $_TBUF_
   :title: $_TBUF_

   A tri-state buffer.
   ::
   
      Truth table:    A E | Y
                     -----+---
                      a 1 | a
                      - 0 | z
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:453

   module \$_TBUF_ (A, E, Y);
       input A, E;
       output Y;
       assign Y = E ? A : 1'bz;
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_TBUF_``.
