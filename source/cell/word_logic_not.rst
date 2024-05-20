$logic_not
==========

.. cell:def:: $logic_not
   :title: $logic_not

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1222

   module \$logic_not (A, Y);
       
       parameter A_SIGNED = 0;
       parameter A_WIDTH = 0;
       parameter Y_WIDTH = 0;
       
       input [A_WIDTH-1:0] A;
       output [Y_WIDTH-1:0] Y;
       
       generate
           if (A_SIGNED) begin:BLOCK1
               assign Y = !$signed(A);
           end else begin:BLOCK2
               assign Y = !A;
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $logic_not``.
