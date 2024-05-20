$_DFF_PP1_
==========

.. cell:def:: $_DFF_PP1_
   :title: $_DFF_PP1_

   A positive edge D-type flip-flop with positive polarity set.
   ::
   
      Truth table:    D C R | Q
                     -------+---
                      - - 1 | 1
                      d / - | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:860

   module \$_DFF_PP1_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(posedge C or posedge R) begin
           if (R == 1)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_PP1_``.
