$_DFFSR_NNN_
============

.. cell:def:: $_DFFSR_NNN_
   :title: $_DFFSR_NNN_

   A negative edge D-type flip-flop with negative polarity set and negative
   polarity reset.
   ::
   
      Truth table:    C S R D | Q
                     ---------+---
                      - - 0 - | 0
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
   :caption: simcells.v:1553

   module \$_DFFSR_NNN_ (C, S, R, D, Q);
       input C, S, R, D;
       output reg Q;
       always @(negedge C, negedge S, negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (S == 0)
               Q <= 1;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFSR_NNN_``.
