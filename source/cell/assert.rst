$assert
=======

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1686

   module \$assert (A, EN);
       
       input A, EN;
       
       `ifndef SIMLIB_NOCHECKS
       always @* begin
           if (A !== 1'b1 && EN === 1'b1) begin
               $display("Assertion %m failed!");
               $stop;
           end
       end
       `endif
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $assert``.
