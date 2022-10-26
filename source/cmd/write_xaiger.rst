==========================================
write_xaiger - write design to XAIGER file
==========================================

.. only:: html

    :code:`yosys> help write_xaiger`
    ----------------------------------------------------------------------------


    :code:`write_xaiger [options] [filename]` ::

        Write the top module (according to the (* top *) attribute or if only one module
        is currently selected) to an XAIGER file. Any non $_NOT_, $_AND_, (optionally
        $_DFF_N_, $_DFF_P_), or non (* abc9_box *) cells will be converted into psuedo-
        inputs and pseudo-outputs. Whitebox contents will be taken from the equivalent
        module in the '$abc9_holes' design, if it exists.


    :code:`-ascii` ::

            write ASCII version of AIGER format


    :code:`-map <filename>` ::

            write an extra file with port and box symbols


    :code:`-dff` ::

            write $_DFF_[NP]_ cells

.. only:: latex

    ::

        
            write_xaiger [options] [filename]
        
        Write the top module (according to the (* top *) attribute or if only one module
        is currently selected) to an XAIGER file. Any non $_NOT_, $_AND_, (optionally
        $_DFF_N_, $_DFF_P_), or non (* abc9_box *) cells will be converted into psuedo-
        inputs and pseudo-outputs. Whitebox contents will be taken from the equivalent
        module in the '$abc9_holes' design, if it exists.
        
            -ascii
                write ASCII version of AIGER format
        
            -map <filename>
                write an extra file with port and box symbols
        
            -dff
                write $_DFF_[NP]_ cells
        
