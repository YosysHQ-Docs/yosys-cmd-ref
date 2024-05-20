$overwrite_tag
==============

.. cell:def:: $overwrite_tag
   :title: $overwrite_tag

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2772

   module \$overwrite_tag (A, SET, CLR);
       
       parameter TAG = "";
       parameter WIDTH = 0;
       
       input [WIDTH-1:0] A;
       input [WIDTH-1:0] SET;
       input [WIDTH-1:0] CLR;
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $overwrite_tag``.
