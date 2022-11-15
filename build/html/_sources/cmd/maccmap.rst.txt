============================
maccmap - mapping macc cells
============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help maccmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        maccmap [-unmap] [selection]

    ::

        This pass maps $macc cells to yosys $fa and $alu cells. When the -unmap option
        is used then the $macc cell is mapped to $add, $sub, etc. cells instead.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            maccmap [-unmap] [selection]
        
        This pass maps $macc cells to yosys $fa and $alu cells. When the -unmap option
        is used then the $macc cell is mapped to $add, $sub, etc. cells instead.
        
