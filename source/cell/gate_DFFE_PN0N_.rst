$_DFFE_PN0N_
============

.. cell:def:: $_DFFE_PN0N_
   :title: $_DFFE_PN0N_

   A positive edge D-type flip-flop with negative polarity reset and negative
   polarity clock enable.
   ::
   
      Truth table:    D C R E | Q
                     ---------+---
                      - - 0 - | 0
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
   :caption: simcells.v:1076

   module \$_DFFE_PN0N_ (D, C, R, E, Q);
       input D, C, R, E;
       output reg Q;
       always @(posedge C or negedge R) begin
           if (R == 0)
               Q <= 0;
           else if (E == 0)
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_PN0N_``.
