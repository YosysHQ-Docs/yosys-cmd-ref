$_DFFE_NN0P_
============

.. cell:def:: $_DFFE_NN0P_
   :title: $_DFFE_NN0P_

   A negative edge D-type flip-flop with negative polarity reset and positive
   polarity clock enable.
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - - 0 - | 0
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
   :caption: simcells.v:908

   module \$_DFFE_NN0P_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(negedge C or negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (E == 1)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_NN0P_``.
