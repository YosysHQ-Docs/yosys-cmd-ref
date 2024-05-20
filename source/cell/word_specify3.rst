$specify3
=========

.. cell:def:: $specify3
   :title: $specify3

   No help message for this cell type found.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:1512

   module \$specify3 (EN, SRC, DST, DAT);
       
       parameter FULL = 0;
       parameter SRC_WIDTH = 1;
       parameter DST_WIDTH = 1;
       
       parameter EDGE_EN = 0;
       parameter EDGE_POL = 0;
       
       parameter SRC_DST_PEN = 0;
       parameter SRC_DST_POL = 0;
       
       parameter DAT_DST_PEN = 0;
       parameter DAT_DST_POL = 0;
       
       parameter T_RISE_MIN = 0;
       parameter T_RISE_TYP = 0;
       parameter T_RISE_MAX = 0;
       
       parameter T_FALL_MIN = 0;
       parameter T_FALL_TYP = 0;
       parameter T_FALL_MAX = 0;
       
       input EN;
       input [SRC_WIDTH-1:0] SRC;
       input [DST_WIDTH-1:0] DST, DAT;
       
       localparam ED = EDGE_EN     ? (EDGE_POL    ? 1 : 2) : 0;
       localparam SD = SRC_DST_PEN ? (SRC_DST_POL ? 1 : 2) : 0;
       localparam DD = DAT_DST_PEN ? (DAT_DST_POL ? 1 : 2) : 0;
       
       `ifdef SIMLIB_SPECIFY
       specify
           // DD=0
       
           if (EN && DD==0 && SD==0 && ED==0 && !FULL) (        SRC  => (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==0 && ED==0 &&  FULL) (        SRC  *> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==0 && ED==1 && !FULL) (posedge SRC  => (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==0 && ED==1 &&  FULL) (posedge SRC  *> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==0 && ED==2 && !FULL) (negedge SRC  => (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==0 && ED==2 &&  FULL) (negedge SRC  *> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           if (EN && DD==0 && SD==1 && ED==0 && !FULL) (        SRC +=> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==1 && ED==0 &&  FULL) (        SRC +*> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==1 && ED==1 && !FULL) (posedge SRC +=> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==1 && ED==1 &&  FULL) (posedge SRC +*> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==1 && ED==2 && !FULL) (negedge SRC +=> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==1 && ED==2 &&  FULL) (negedge SRC +*> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           if (EN && DD==0 && SD==2 && ED==0 && !FULL) (        SRC -=> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==2 && ED==0 &&  FULL) (        SRC -*> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==2 && ED==1 && !FULL) (posedge SRC -=> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==2 && ED==1 &&  FULL) (posedge SRC -*> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==2 && ED==2 && !FULL) (negedge SRC -=> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==0 && SD==2 && ED==2 &&  FULL) (negedge SRC -*> (DST  : DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           // DD=1
       
           if (EN && DD==1 && SD==0 && ED==0 && !FULL) (        SRC  => (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==0 && ED==0 &&  FULL) (        SRC  *> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==0 && ED==1 && !FULL) (posedge SRC  => (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==0 && ED==1 &&  FULL) (posedge SRC  *> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==0 && ED==2 && !FULL) (negedge SRC  => (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==0 && ED==2 &&  FULL) (negedge SRC  *> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           if (EN && DD==1 && SD==1 && ED==0 && !FULL) (        SRC +=> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==1 && ED==0 &&  FULL) (        SRC +*> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==1 && ED==1 && !FULL) (posedge SRC +=> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==1 && ED==1 &&  FULL) (posedge SRC +*> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==1 && ED==2 && !FULL) (negedge SRC +=> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==1 && ED==2 &&  FULL) (negedge SRC +*> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           if (EN && DD==1 && SD==2 && ED==0 && !FULL) (        SRC -=> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==2 && ED==0 &&  FULL) (        SRC -*> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==2 && ED==1 && !FULL) (posedge SRC -=> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==2 && ED==1 &&  FULL) (posedge SRC -*> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==2 && ED==2 && !FULL) (negedge SRC -=> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==1 && SD==2 && ED==2 &&  FULL) (negedge SRC -*> (DST +: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           // DD=2
       
           if (EN && DD==2 && SD==0 && ED==0 && !FULL) (        SRC  => (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==0 && ED==0 &&  FULL) (        SRC  *> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==0 && ED==1 && !FULL) (posedge SRC  => (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==0 && ED==1 &&  FULL) (posedge SRC  *> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==0 && ED==2 && !FULL) (negedge SRC  => (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==0 && ED==2 &&  FULL) (negedge SRC  *> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           if (EN && DD==2 && SD==1 && ED==0 && !FULL) (        SRC +=> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==1 && ED==0 &&  FULL) (        SRC +*> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==1 && ED==1 && !FULL) (posedge SRC +=> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==1 && ED==1 &&  FULL) (posedge SRC +*> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==1 && ED==2 && !FULL) (negedge SRC +=> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==1 && ED==2 &&  FULL) (negedge SRC +*> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       
           if (EN && DD==2 && SD==2 && ED==0 && !FULL) (        SRC -=> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==2 && ED==0 &&  FULL) (        SRC -*> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==2 && ED==1 && !FULL) (posedge SRC -=> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==2 && ED==1 &&  FULL) (posedge SRC -*> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==2 && ED==2 && !FULL) (negedge SRC -=> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
           if (EN && DD==2 && SD==2 && ED==2 &&  FULL) (negedge SRC -*> (DST -: DAT)) = (T_RISE_MIN:T_RISE_TYP:T_RISE_MAX, T_FALL_MIN:T_FALL_TYP:T_FALL_MAX);
       endspecify
       `endif
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $specify3``.
