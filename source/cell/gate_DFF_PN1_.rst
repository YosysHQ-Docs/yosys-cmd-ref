$_DFF_PN1_
==========

.. cell:def:: $_DFF_PN1_
   :title: $_DFF_PN1_

   A positive edge D-type flip-flop with negative polarity set.
   ::
   
      Truth table:    D C R | Q
                     -------+---
                      - - 0 | 1
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
   :caption: simcells.v:814

   module \$_DFF_PN1_ (D, C, R, Q);
       input D, C, R;
       output reg Q;
       always @(posedge C or negedge R) begin
           if (R == 0)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFF_PN1_``.
