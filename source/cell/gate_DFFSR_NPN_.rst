$_DFFSR_NPN_
============

.. cell:def:: $_DFFSR_NPN_
   :title: $_DFFSR_NPN_

   A negative edge D-type flip-flop with positive polarity set and negative
   polarity reset.
   ::
   
      Truth table:    C S R D | Q
                     ---------+---
                      - - 0 - | 0
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
   :caption: simcells.v:1607

   module \$_DFFSR_NPN_ (C, S, R, D, Q);
       input C, S, R, D;
       output reg Q;
       always @(negedge C, posedge S, negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (S == 1)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSR_NPN_``.
