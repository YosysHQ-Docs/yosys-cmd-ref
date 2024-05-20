$_DFF_N_
========

.. cell:def:: $_DFF_N_
   :title: $_DFF_N_

   A negative edge D-type flip-flop.
   ::
   
      Truth table:    D C | Q
                     -----+---
                      d \ | d
                      - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:584

   module \$_DFF_N_ (D, C, Q);
       input D, C;
       output reg Q;
       always @(negedge C) begin
           Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_N_``.
