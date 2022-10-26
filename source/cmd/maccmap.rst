============================
maccmap - mapping macc cells
============================

.. only:: html

    :code:`yosys> help maccmap`
    ----------------------------------------------------------------------------


    :code:`maccmap [-unmap] [selection]` ::

        This pass maps $macc cells to yosys $fa and $alu cells. When the -unmap option
        is used then the $macc cell is mapped to $add, $sub, etc. cells instead.

.. only:: latex

    ::

        
            maccmap [-unmap] [selection]
        
        This pass maps $macc cells to yosys $fa and $alu cells. When the -unmap option
        is used then the $macc cell is mapped to $add, $sub, etc. cells instead.
        
