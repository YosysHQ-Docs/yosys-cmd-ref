====================================================
pmux2shiftx - transform $pmux cells to $shiftx cells
====================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help pmux2shiftx`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        pmux2shiftx [options] [selection]

    ::

        This pass transforms $pmux cells to $shiftx cells.


    .. code:: yoscrypt

        -v, -vv

    ::

            verbose output


    .. code:: yoscrypt

        -min_density <percentage>

    ::

            specifies the minimum density for the shifter
            default: 50


    .. code:: yoscrypt

        -min_choices <int>

    ::

            specified the minimum number of choices for a control signal
            default: 3


    .. code:: yoscrypt

        -onehot ignore|pmux|shiftx

    ::

            select strategy for one-hot encoded control signals
            default: pmux


    .. code:: yoscrypt

        -norange

    ::

            disable $sub inference for "range decoders"

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            pmux2shiftx [options] [selection]
        
        This pass transforms $pmux cells to $shiftx cells.
        
            -v, -vv
                verbose output
        
            -min_density <percentage>
                specifies the minimum density for the shifter
                default: 50
        
            -min_choices <int>
                specified the minimum number of choices for a control signal
                default: 3
        
            -onehot ignore|pmux|shiftx
                select strategy for one-hot encoded control signals
                default: pmux
        
            -norange
                disable $sub inference for "range decoders"
        
