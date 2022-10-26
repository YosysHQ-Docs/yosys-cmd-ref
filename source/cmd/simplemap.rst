=============================================
simplemap - mapping simple coarse-grain cells
=============================================

.. only:: html

    :code:`yosys> help simplemap`
    ----------------------------------------------------------------------------


    :code:`simplemap [selection]` ::

        This pass maps a small selection of simple coarse-grain cells to yosys gate
        primitives. The following internal cell types are mapped by this pass:

          $not, $pos, $and, $or, $xor, $xnor
          $reduce_and, $reduce_or, $reduce_xor, $reduce_xnor, $reduce_bool
          $logic_not, $logic_and, $logic_or, $mux, $tribuf
          $sr, $ff, $dff, $dffe, $dffsr, $dffsre, $adff, $adffe, $aldff, $aldffe, $sdff,
          $sdffe, $sdffce, $dlatch, $adlatch, $dlatchsr

.. only:: latex

    ::

        
            simplemap [selection]
        
        This pass maps a small selection of simple coarse-grain cells to yosys gate
        primitives. The following internal cell types are mapped by this pass:
        
          $not, $pos, $and, $or, $xor, $xnor
          $reduce_and, $reduce_or, $reduce_xor, $reduce_xnor, $reduce_bool
          $logic_not, $logic_and, $logic_or, $mux, $tribuf
          $sr, $ff, $dff, $dffe, $dffsr, $dffsre, $adff, $adffe, $aldff, $aldffe, $sdff,
          $sdffe, $sdffce, $dlatch, $adlatch, $dlatchsr
        
