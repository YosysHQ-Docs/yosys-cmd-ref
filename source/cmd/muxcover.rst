====================================================
muxcover - cover trees of MUX cells with wider MUXes
====================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: muxcover
    :title: cover trees of MUX cells with wider MUXes



    .. code:: yoscrypt

        muxcover [options] [selection]

    ::

        Cover trees of $_MUX_ cells with $_MUX{4,8,16}_ cells


    .. code:: yoscrypt

        -mux4[=cost], -mux8[=cost], -mux16[=cost]

    ::

            Cover $_MUX_ trees using the specified types of MUXes (with optional
            integer costs). If none of these options are given, the effect is the
            same as if all of them are.
            Default costs: $_MUX4_ = 220, $_MUX8_ = 460, 
                           $_MUX16_ = 940


    .. code:: yoscrypt

        -mux2=cost

    ::

            Use the specified cost for $_MUX_ cells when making covering decisions.
            Default cost: $_MUX_ = 100


    .. code:: yoscrypt

        -dmux=cost

    ::

            Use the specified cost for $_MUX_ cells used in decoders.
            Default cost: 90


    .. code:: yoscrypt

        -nodecode

    ::

            Do not insert decoder logic. This reduces the number of possible
            substitutions, but guarantees that the resulting circuit is not
            less efficient than the original circuit.


    .. code:: yoscrypt

        -nopartial

    ::

            Do not consider mappings that use $_MUX<N>_ to select from less
            than <N> different signals.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            muxcover [options] [selection]
        
        Cover trees of $_MUX_ cells with $_MUX{4,8,16}_ cells
        
            -mux4[=cost], -mux8[=cost], -mux16[=cost]
                Cover $_MUX_ trees using the specified types of MUXes (with optional
                integer costs). If none of these options are given, the effect is the
                same as if all of them are.
                Default costs: $_MUX4_ = 220, $_MUX8_ = 460, 
                               $_MUX16_ = 940
        
            -mux2=cost
                Use the specified cost for $_MUX_ cells when making covering decisions.
                Default cost: $_MUX_ = 100
        
            -dmux=cost
                Use the specified cost for $_MUX_ cells used in decoders.
                Default cost: 90
        
            -nodecode
                Do not insert decoder logic. This reduces the number of possible
                substitutions, but guarantees that the resulting circuit is not
                less efficient than the original circuit.
        
            -nopartial
                Do not consider mappings that use $_MUX<N>_ to select from less
                than <N> different signals.
        
