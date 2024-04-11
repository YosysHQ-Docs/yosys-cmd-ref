================================================
aigmap - map logic to and-inverter-graph circuit
================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: aigmap
    :title: map logic to and-inverter-graph circuit



    .. code:: yoscrypt

        aigmap [options] [selection]

    ::

        Replace all logic cells with circuits made of only $_AND_ and
        $_NOT_ cells.


    .. code:: yoscrypt

        -nand

    ::

            Enable creation of $_NAND_ cells


    .. code:: yoscrypt

        -select

    ::

            Overwrite replaced cells in the current selection with new $_AND_,
            $_NOT_, and $_NAND_, cells

.. raw:: latex

    \end{comment}

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
        
