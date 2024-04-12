$initstate
==========

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1744

   module \$initstate (Y);
       
       output reg Y = 1;
       reg [3:0] cnt = 1;
       reg trig = 0;
       
       initial trig <= 1;
       
       always @(cnt, trig) begin
           Y <= |cnt;
           cnt <= cnt + |cnt;
       end
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $initstate``.
