====================================
dffinit - set INIT param on FF cells
====================================

.. only:: html

    :code:`yosys> help dffinit`
    ----------------------------------------------------------------------------


    :code:`dffinit [options] [selection]` ::

        This pass sets an FF cell parameter to the the initial value of the net it
        drives. (This is primarily used in FPGA flows.)


    :code:`-ff <cell_name> <output_port> <init_param>` ::

            operate on the specified cell type. this option can be used
            multiple times.


    :code:`-highlow` ::

            use the string values "high" and "low" to represent a single-bit
            initial value of 1 or 0. (multi-bit values are not supported in this
            mode.)


    :code:`-strinit <string for high> <string for low>` ::

            use string values in the command line to represent a single-bit
            initial value of 1 or 0. (multi-bit values are not supported in this
            mode.)


    :code:`-noreinit` ::

            fail if the FF cell has already a defined initial value set in other
            passes and the initial value of the net it drives is not equal to
            the already defined initial value.

.. only:: latex

    ::

        
            dffinit [options] [selection]
        
        This pass sets an FF cell parameter to the the initial value of the net it
        drives. (This is primarily used in FPGA flows.)
        
            -ff <cell_name> <output_port> <init_param>
                operate on the specified cell type. this option can be used
                multiple times.
        
            -highlow
                use the string values "high" and "low" to represent a single-bit
                initial value of 1 or 0. (multi-bit values are not supported in this
                mode.)
        
            -strinit <string for high> <string for low> 
                use string values in the command line to represent a single-bit
                initial value of 1 or 0. (multi-bit values are not supported in this
                mode.)
        
            -noreinit
                fail if the FF cell has already a defined initial value set in other
                passes and the initial value of the net it drives is not equal to
                the already defined initial value.
        
