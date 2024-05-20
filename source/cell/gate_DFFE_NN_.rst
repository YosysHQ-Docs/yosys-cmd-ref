$_DFFE_NN_
==========

.. cell:def:: $_DFFE_NN_
   :title: $_DFFE_NN_

   A negative edge D-type flip-flop with negative polarity enable.
   ::
   
      Truth table:    D C E | Q
                     -------+---
                      d \ 0 | d
                      - - - | q
      

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: false

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:622

   module \$_DFFE_NN_ (D, C, E, Q);
       input D, C, E;
       output reg Q;
       always @(negedge C) begin
           if (!E) Q <= D;
       end
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_DFFE_NN_``.
