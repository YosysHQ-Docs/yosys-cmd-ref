===========================================
read_liberty - read cells from liberty file
===========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help read_liberty`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        read_liberty [filename]

    ::

        Read cells from liberty file as modules into current design.


    .. code:: yoscrypt

        -lib

    ::

            only create empty blackbox modules


    .. code:: yoscrypt

        -wb

    ::

            mark imported cells as whiteboxes


    .. code:: yoscrypt

        -nooverwrite

    ::

            ignore re-definitions of modules. (the default behavior is to
            create an error message if the existing module is not a blackbox
            module, and overwrite the existing module if it is  a blackbox module.)


    .. code:: yoscrypt

        -overwrite

    ::

            overwrite existing modules with the same name


    .. code:: yoscrypt

        -ignore_miss_func

    ::

            ignore cells with missing function specification of outputs


    .. code:: yoscrypt

        -ignore_miss_dir

    ::

            ignore cells with a missing or invalid direction
            specification on a pin


    .. code:: yoscrypt

        -ignore_miss_data_latch

    ::

            ignore latches with missing data and/or enable pins


    .. code:: yoscrypt

        -setattr <attribute_name>

    ::

            set the specified attribute (to the value 1) on all loaded modules

.. raw:: latex

    \end{comment}

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
        
