$set_tag
========

.. cell:def:: $set_tag
   :title: $set_tag

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2742

   module \$set_tag (A, SET, CLR, Y);
       
       parameter TAG = "";
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] A;
       input [WIDTH-1:0] SET;
       input [WIDTH-1:0] CLR;
       output [WIDTH-1:0] Y;
       
       assign Y = A;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $set_tag``.
