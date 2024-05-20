$_DFFE_PP0N_
============

.. cell:def:: $_DFFE_PP0N_
   :title: $_DFFE_PP0N_

   A positive edge D-type flip-flop with positive polarity reset and negative
   polarity clock enable.
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - - 1 - | 0
                      d / - 0 | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1172

   module \$_DFFE_PP0N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C or posedge R) begin
           if (R == 1)
               Q <= 0;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_PP0N_``.
