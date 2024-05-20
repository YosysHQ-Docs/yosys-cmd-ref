$get_tag
========

.. cell:def:: $get_tag
   :title: $get_tag

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2758

   module \$get_tag (A, Y);
       
       parameter TAG = "";
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] A;
       output [WIDTH-1:0] Y;
       
       assign Y = A;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $get_tag``.
