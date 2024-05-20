$_DFFE_NP1N_
============

.. cell:def:: $_DFFE_NP1N_
   :title: $_DFFE_NP1N_

   A negative edge D-type flip-flop with positive polarity set and negative
   polarity clock enable.
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - - 1 - | 1
                      d \ - 0 | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1028

   module \$_DFFE_NP1N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C or posedge R) begin
           if (R == 1)
               Q <= 1;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_NP1N_``.
