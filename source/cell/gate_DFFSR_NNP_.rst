$_DFFSR_NNP_
============

.. cell:def:: $_DFFSR_NNP_
   :title: $_DFFSR_NNP_

   A negative edge D-type flip-flop with negative polarity set and positive
   polarity reset.
   ::
   
      Truth table:    C S R D | Q
                     ---------+---
                      - - 1 - | 0
                      - 0 - - | 1
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
   :caption: simcells.v:1580

   module \$_DFFSR_NNP_ (C, S, R, D, Q);
       input C, S, R, D;
       output reg Q;
       always @(negedge C, negedge S, posedge R) begin
           if (R == 1)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSR_NNP_``.
