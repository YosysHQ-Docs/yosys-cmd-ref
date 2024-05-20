$demux
======

.. cell:def:: $demux
   :title: $demux

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1396

   module \$demux (A, S, Y);
       
       parameter WIDTH = 1;
       parameter S_WIDTH = 1;
       
       input [WIDTH-1:0] A;
       input [S_WIDTH-1:0] S;
       output [(WIDTH << S_WIDTH)-1:0] Y;
       
       genvar i;
       generate
           for (i = 0; i < (1 << S_WIDTH); i = i + 1) begin:slices
               assign Y[i*WIDTH+:WIDTH] = (S == i) ? A : 0;
           end
       endgenerate
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $demux``.
