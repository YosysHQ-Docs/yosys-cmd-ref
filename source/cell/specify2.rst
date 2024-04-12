$specify2
=========

No help message for this cell type found.

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1474

   module \$specify2 (EN, SRC, DST);
       
       parameter FULL = 0;
       parameter SRC_WIDTH = 1;
       parameter DST_WIDTH = 1;
       
       parameter SRC_DST_PEN = 0;
       parameter SRC_DST_POL = 0;
       
       parameter T_RISE_MIN = 0;
       parameter T_RISE_TYP = 0;
       parameter T_RISE_MAX = 0;
       
       parameter T_FALL_MIN = 0;
       parameter T_FALL_TYP = 0;
       parameter T_FALL_MAX = 0;
       
       input EN;
       input [SRC_WIDTH-1:0] SRC;
       input [DST_WIDTH-1:0] DST;
       
       localparam SD = SRC_DST_PEN ? (SRC_DST_POL ? 1 : 2) : 0;
       
       `ifdef SIMLIB_SPECIFY
       specify
           if (EN && SD==0 && !FULL) (SRC  => DST) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && SD==0 &&  FULL) (SRC  *> DST) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && SD==1 && !FULL) (SRC +=> DST) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && SD==1 &&  FULL) (SRC +*> DST) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && SD==2 && !FULL) (SRC -=> DST) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && SD==2 &&  FULL) (SRC -*> DST) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       endspecify
       `endif
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $specify2``.
