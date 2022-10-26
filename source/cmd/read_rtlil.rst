=========================================
read_rtlil - read modules from RTLIL file
=========================================

.. only:: html

    :code:`yosys> help read_rtlil`
    ----------------------------------------------------------------------------


    :code:`read_rtlil [filename]` ::

        Load modules from an RTLIL file to the current design. (RTLIL is a text
        representation of a design in yosys's internal format.)


    :code:`-nooverwrite` ::

            ignore re-definitions of modules. (the default behavior is to
            create an error message if the existing module is not a blackbox
            module, and overwrite the existing module if it is a blackbox module.)


    :code:`-overwrite` ::

            overwrite existing modules with the same name


    :code:`-lib` ::

            only create empty blackbox modules

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
        
