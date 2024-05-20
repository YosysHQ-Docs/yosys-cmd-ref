$_ALDFF_PP_
===========

.. cell:def:: $_ALDFF_PP_
   :title: $_ALDFF_PP_

   A positive edge D-type flip-flop with positive polarity async load.
   ::
   
      Truth table:    D C L AD | Q
                     ----------+---
                      - - 1 a  | a
                      d / - -  | d
                      - - - -  | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:1336

   module \$_ALDFF_PP_ (D, C, L, AD, Q);
       input D, C, L, AD;
       output reg Q;
       always @(posedge C or posedge L) begin
           if (L == 1)
               Q <= AD;
           else
               Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_ALDFF_PP_``.
