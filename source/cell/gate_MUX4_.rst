$_MUX4_
=======

.. cell:def:: $_MUX4_
   :title: $_MUX4_

   A 4-input MUX gate.
   ::
   
      Truth table:    A B C D S T | Y
                     -------------+---
                      a - - - 0 0 | a
                      - b - - 1 0 | b
                      - - c - 0 1 | c
                      - - - d 1 1 | d
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:263

   module \$_MUX4_ (A, B, C, D, S, T, Y);
       input A, B, C, D, S, T;
       output Y;
       assign Y = T ? (S ? D : C) :
                      (S ? B : A);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_MUX4_``.
