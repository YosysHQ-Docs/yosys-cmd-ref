$allseq
=======

.. cell:def:: $allseq
   :title: $allseq

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1817

   module \$allseq (Y);
       
       parameter WIDTH = 0;
       
       output [WIDTH-1:0] Y;
       
       assign Y = 'bx;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $allseq``.
