====================================================
pmux2shiftx - transform $pmux cells to $shiftx cells
====================================================

.. only:: html

    :code:`yosys> help pmux2shiftx`
    ----------------------------------------------------------------------------


    :code:`pmux2shiftx [options] [selection]` ::

        This pass transforms $pmux cells to $shiftx cells.


    :code:`-v, -vv` ::

            verbose output


    :code:`-min_density <percentage>` ::

            specifies the minimum density for the shifter
            default: 50


    :code:`-min_choices <int>` ::

            specified the minimum number of choices for a control signal
            default: 3


    :code:`-onehot ignore|pmux|shiftx` ::

            select strategy for one-hot encoded control signals
            default: pmux


    :code:`-norange` ::

            disable $sub inference for "range decoders"

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
        
