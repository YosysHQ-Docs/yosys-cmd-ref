============================
stat - print some statistics
============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help stat`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        stat [options] [selection]

    ::

        Print some statistics (number of objects) on the selected portion of the
        design.


    .. code:: yoscrypt

        -top <module>

    ::

            print design hierarchy with this module as top. if the design is fully
            selected and a module has the 'top' attribute set, this module is used
            default value for this option.


    .. code:: yoscrypt

        -liberty <liberty_file>

    ::

            use cell area information from the provided liberty file


    .. code:: yoscrypt

        -tech <technology>

    ::

            print area estemate for the specified technology. Currently supported
            values for <technology>: xilinx, cmos


    .. code:: yoscrypt

        -width

    ::

            annotate internal cell types with their word width.
            e.g. $add_8 for an 8 bit wide $add cell.


    .. code:: yoscrypt

        -json

    ::

            output the statistics in a machine-readable JSON format.
            this is output to the console; use "tee" to output to a file.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            stat [options] [selection]
        
        Print some statistics (number of objects) on the selected portion of the
        design.
        
            -top <module>
                print design hierarchy with this module as top. if the design is fully
                selected and a module has the 'top' attribute set, this module is used
                default value for this option.
        
            -liberty <liberty_file>
                use cell area information from the provided liberty file
        
            -tech <technology>
                print area estemate for the specified technology. Currently supported
                values for <technology>: xilinx, cmos
        
            -width
                annotate internal cell types with their word width.
                e.g. $add_8 for an 8 bit wide $add cell.
        
            -json
                output the statistics in a machine-readable JSON format.
                this is output to the console; use "tee" to output to a file.
        
