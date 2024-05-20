$_ALDFF_NN_
===========

.. cell:def:: $_ALDFF_NN_
   :title: $_ALDFF_NN_

   A negative edge D-type flip-flop with negative polarity async load.
   ::
   
      Truth table:    D C L AD | Q
                     ----------+---
                      - - 0 a  | a
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
   :caption: simcells.v:1267

   module \$_ALDFF_NN_ (D, C, L, AD, Q);
       input D, C, L, AD;
       output reg Q;
       always @(negedge C or negedge L) begin
           if (L == 0)
               Q <= AD;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFF_NN_``.
