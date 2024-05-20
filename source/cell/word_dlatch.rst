$dlatch
=======

.. cell:def:: $dlatch
   :title: $dlatch

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:2216

   module \$dlatch (EN, D, Q);
       
       parameter WIDTH = 0;
       parameter EN_POLARITY = 1'b1;
       
       input EN;
       input [WIDTH-1:0] D;
       output reg [WIDTH-1:0] Q;
       
       always @* begin
           if (EN == EN_POLARITY)
               Q = D;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $dlatch``.
