$_DFFE_PP1P_
============

.. cell:def:: $_DFFE_PP1P_
   :title: $_DFFE_PP1P_

   A positive edge D-type flip-flop with positive polarity set and positive
   polarity clock enable.
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - - 1 - | 1
                      d / - 1 | d
                      - - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1244

   module \$_DFFE_PP1P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C or posedge R) begin
           if (R == 1)
               Q <= 1;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_PP1P_``.
