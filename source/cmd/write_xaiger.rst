==========================================
write_xaiger - write design to XAIGER file
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: write_xaiger
    :title: write design to XAIGER file



    .. code:: yoscrypt

        write_xaiger [options] [filename]

    ::

        Write the top module (according to the (* top *) attribute or if only one module
        is currently selected) to an XAIGER file. Any non $_NOT_, $_AND_, (optionally
        $_DFF_N_, $_DFF_P_), or non (* abc9_box *) cells will be converted into psuedo-
        inputs and pseudo-outputs. Whitebox contents will be taken from the equivalent
        module in the '$abc9_holes' design, if it exists.


    .. code:: yoscrypt

        -ascii

    ::

            write ASCII version of AIGER format


    .. code:: yoscrypt

        -map <filename>

    ::

            write an extra file with port and box symbols


    .. code:: yoscrypt

        -dff

    ::

            write $_DFF_[NP]_ cells

.. raw:: latex

    \end{comment}

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
        
