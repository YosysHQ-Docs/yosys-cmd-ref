$_DFFE_NP0P_
============

.. cell:def:: $_DFFE_NP0P_
   :title: $_DFFE_NP0P_

   A negative edge D-type flip-flop with positive polarity reset and positive
   polarity clock enable.
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - - 1 - | 0
                      d \ - 1 | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1004

   module \$_DFFE_NP0P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C or posedge R) begin
           if (R == 1)
               Q <= 0;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_NP0P_``.
