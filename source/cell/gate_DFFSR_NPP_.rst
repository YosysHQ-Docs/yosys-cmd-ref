$_DFFSR_NPP_
============

.. cell:def:: $_DFFSR_NPP_
   :title: $_DFFSR_NPP_

   A negative edge D-type flip-flop with positive polarity set and positive
   polarity reset.
   ::
   
      Truth table:    C S R D | Q
                     ---------+---
                      - - 1 - | 0
                      - 1 - - | 1
                      \ - - d | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1634

   module \$_DFFSR_NPP_ (C, S, R, D, Q);
       input C, S, R, D;
       output reg Q;
       always @(negedge C, posedge S, posedge R) begin
           if (R == 1)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSR_NPP_``.
