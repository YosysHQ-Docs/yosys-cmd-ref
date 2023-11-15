=======================================
opt_lut_ins - discard unused LUT inputs
=======================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: opt_lut_ins
    :title: discard unused LUT inputs



    .. code:: yoscrypt

        opt_lut_ins [options] [selection]

    ::

        This pass removes unused inputs from LUT cells (that is, inputs that can not
        influence the output signal given this LUT's value).  While such LUTs cannot
        be directly emitted by ABC, they can be a result of various post-ABC
        transformations, such as mapping wide LUTs (not all sub-LUTs will use the
        full set of inputs) or optimizations such as xilinx_dffopt.


    .. code:: yoscrypt

        -tech <technology>

    ::

            Instead of generic $lut cells, operate on LUT cells specific
            to the given technology.  Valid values are: xilinx, lattice, gowin.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            opt_lut_ins [options] [selection]
        
        This pass removes unused inputs from LUT cells (that is, inputs that can not
        influence the output signal given this LUT's value).  While such LUTs cannot
        be directly emitted by ABC, they can be a result of various post-ABC
        transformations, such as mapping wide LUTs (not all sub-LUTs will use the
        full set of inputs) or optimizations such as xilinx_dffopt.
        
            -tech <technology>
                Instead of generic $lut cells, operate on LUT cells specific
                to the given technology.  Valid values are: xilinx, lattice, gowin.
        
