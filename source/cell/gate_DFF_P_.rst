$_DFF_P_
========

.. cell:def:: $_DFF_P_
   :title: $_DFF_P_

   A positive edge D-type flip-flop.
   ::
   
      Truth table:    D C | Q
                     -----+---
                      d / | d
                      - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:603

   module \$_DFF_P_ (D, C, Q);
       input D, C;
       output reg Q;
       always @(posedge C) begin
           Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_P_``.
