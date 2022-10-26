===========================================
read_liberty - read cells from liberty file
===========================================

.. only:: html

    :code:`yosys> help read_liberty`
    ----------------------------------------------------------------------------


    :code:`read_liberty [filename]` ::

        Read cells from liberty file as modules into current design.


    :code:`-lib` ::

            only create empty blackbox modules


    :code:`-wb` ::

            mark imported cells as whiteboxes


    :code:`-nooverwrite` ::

            ignore re-definitions of modules. (the default behavior is to
            create an error message if the existing module is not a blackbox
            module, and overwrite the existing module if it is  a blackbox module.)


    :code:`-overwrite` ::

            overwrite existing modules with the same name


    :code:`-ignore_miss_func` ::

            ignore cells with missing function specification of outputs


    :code:`-ignore_miss_dir` ::

            ignore cells with a missing or invalid direction
            specification on a pin


    :code:`-ignore_miss_data_latch` ::

            ignore latches with missing data and/or enable pins


    :code:`-setattr <attribute_name>` ::

            set the specified attribute (to the value 1) on all loaded modules

.. only:: latex

    ::

        
            read_liberty [filename]
        
        Read cells from liberty file as modules into current design.
        
            -lib
                only create empty blackbox modules
        
            -wb
                mark imported cells as whiteboxes
        
            -nooverwrite
                ignore re-definitions of modules. (the default behavior is to
                create an error message if the existing module is not a blackbox
                module, and overwrite the existing module if it is  a blackbox module.)
        
            -overwrite
                overwrite existing modules with the same name
        
            -ignore_miss_func
                ignore cells with missing function specification of outputs
        
            -ignore_miss_dir
                ignore cells with a missing or invalid direction
                specification on a pin
        
            -ignore_miss_data_latch
                ignore latches with missing data and/or enable pins
        
            -setattr <attribute_name>
                set the specified attribute (to the value 1) on all loaded modules
        
