================================================
aigmap - map logic to and-inverter-graph circuit
================================================

.. only:: html

    :code:`yosys> help aigmap`
    ----------------------------------------------------------------------------


    :code:`aigmap [options] [selection]` ::

        Replace all logic cells with circuits made of only $_AND_ and
        $_NOT_ cells.


    :code:`-nand` ::

            Enable creation of $_NAND_ cells


    :code:`-select` ::

            Overwrite replaced cells in the current selection with new $_AND_,
            $_NOT_, and $_NAND_, cells

.. only:: latex

    ::

        
            aigmap [options] [selection]
        
        Replace all logic cells with circuits made of only $_AND_ and
        $_NOT_ cells.
        
            -nand
                Enable creation of $_NAND_ cells
        
            -select
                Overwrite replaced cells in the current selection with new $_AND_,
                $_NOT_, and $_NAND_, cells
        
