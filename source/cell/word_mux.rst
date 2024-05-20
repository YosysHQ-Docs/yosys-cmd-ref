$mux
====

.. cell:def:: $mux
   :title: $mux

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1321

   module \$mux (A, B, S, Y);
       
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] A, B;
       input S;
       output [WIDTH-1:0] Y;
       
       assign Y = S ? B : A;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $mux``.
