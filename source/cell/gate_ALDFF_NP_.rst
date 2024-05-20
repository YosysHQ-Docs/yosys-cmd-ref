$_ALDFF_NP_
===========

.. cell:def:: $_ALDFF_NP_
   :title: $_ALDFF_NP_

   A negative edge D-type flip-flop with positive polarity async load.
   ::
   
      Truth table:    D C L AD | Q
                     ----------+---
                      - - 1 a  | a
                      d \ - -  | d
                      - - - -  | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1290

   module \$_ALDFF_NP_ (D, C, L, AD, Q);
       input D, C, L, AD;
       output reg Q;
       always @(negedge C or posedge L) begin
           if (L == 1)
               Q <= AD;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFF_NP_``.
