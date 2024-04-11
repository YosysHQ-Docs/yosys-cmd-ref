=========================================
read_rtlil - read modules from RTLIL file
=========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: read_rtlil
    :title: read modules from RTLIL file



    .. code:: yoscrypt

        read_rtlil [filename]

    ::

        Load modules from an RTLIL file to the current design. (RTLIL is a text
        representation of a design in yosys's internal format.)


    .. code:: yoscrypt

        -nooverwrite

    ::

            ignore re-definitions of modules. (the default behavior is to
            create an error message if the existing module is not a blackbox
            module, and overwrite the existing module if it is a blackbox module.)


    .. code:: yoscrypt

        -overwrite

    ::

            overwrite existing modules with the same name


    .. code:: yoscrypt

        -lib

    ::

            only create empty blackbox modules

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            read_rtlil [filename]
        
        Load modules from an RTLIL file to the current design. (RTLIL is a text
        representation of a design in yosys's internal format.)
        
            -nooverwrite
                ignore re-definitions of modules. (the default behavior is to
                create an error message if the existing module is not a blackbox
                module, and overwrite the existing module if it is a blackbox module.)
        
            -overwrite
                overwrite existing modules with the same name
        
            -lib
                only create empty blackbox modules
        
