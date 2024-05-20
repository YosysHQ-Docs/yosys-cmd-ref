$_DFFE_NP_
==========

.. cell:def:: $_DFFE_NP_
   :title: $_DFFE_NP_

   A negative edge D-type flip-flop with positive polarity enable.
   ::
   
      Truth table:    D C E | Q
                     -------+---
                      d \ 1 | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:641

   module \$_DFFE_NP_ (D, C, E, Q);
       input D, C, E;
       output reg Q;
       always @(negedge C) begin
           if (E) Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_NP_``.
