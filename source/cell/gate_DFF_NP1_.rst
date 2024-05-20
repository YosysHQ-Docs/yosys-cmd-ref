$_DFF_NP1_
==========

.. cell:def:: $_DFF_NP1_
   :title: $_DFF_NP1_

   A negative edge D-type flip-flop with positive polarity set.
   ::
   
      Truth table:    D C R | Q
                     -------+---
                      - - 1 | 1
                      d \ - | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:768

   module \$_DFF_NP1_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(negedge C or posedge R) begin
           if (R == 1)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_NP1_``.
