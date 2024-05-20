$adlatch
========

.. cell:def:: $adlatch
   :title: $adlatch

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2234

   module \$adlatch (EN, ARST, D, Q);
       
       parameter WIDTH = 0;
       parameter EN_POLARITY = 1'b1;
       parameter ARST_POLARITY = 1'b1;
       parameter ARST_VALUE = 0;
       
       input EN, ARST;
       input [WIDTH-1:0] D;
       output reg [WIDTH-1:0] Q;
       
       always @* begin
           if (ARST == ARST_POLARITY)
               Q = ARST_VALUE;
           else if (EN == EN_POLARITY)
               Q = D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $adlatch``.
