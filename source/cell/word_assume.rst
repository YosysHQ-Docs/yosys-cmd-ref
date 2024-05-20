$assume
=======

.. cell:def:: $assume
   :title: $assume

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1703

   module \$assume (A, EN);
       
       input A, EN;
       
       `ifndef SIMLIB_NOCHECKS
       always @* begin
           if (A !== 1'b1 && EN === 1'b1) begin
               $display("Assumption %m failed!");
               $stop;
           end
       end
       `endif
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $assume``.
