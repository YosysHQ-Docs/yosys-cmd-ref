==============================================
write_edif - write design to EDIF netlist file
==============================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_edif`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_edif [options] [filename]

    ::

        Write the current design to an EDIF netlist file.


    .. code:: yoscrypt

        -top top_module

    ::

            set the specified module as design top module


    .. code:: yoscrypt

        -nogndvcc

    ::

            do not create "GND" and "VCC" cells. (this will produce an error
            if the design contains constant nets. use "hilomap" to map to custom
            constant drivers first)


    .. code:: yoscrypt

        -gndvccy

    ::

            create "GND" and "VCC" cells with "Y" outputs. (the default is
            "G" for "GND" and "P" for "VCC".)


    .. code:: yoscrypt

        -attrprop

    ::

            create EDIF properties for cell attributes


    .. code:: yoscrypt

        -keep

    ::

            create extra KEEP nets by allowing a cell to drive multiple nets.


    .. code:: yoscrypt

        -pvector {par|bra|ang}

    ::

            sets the delimiting character for module port rename clauses to
            parentheses, square brackets, or angle brackets.


    .. code:: yoscrypt

        -lsbidx

    ::

            use index 0 for the LSB bit of a net or port instead of MSB.


    ::

        Unfortunately there are different "flavors" of the EDIF file format. This
        command generates EDIF files for the Xilinx place&route tools. It might be
        necessary to make small modifications to this command when a different tool
        is targeted.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_edif [options] [filename]
        
        Write the current design to an EDIF netlist file.
        
            -top top_module
                set the specified module as design top module
        
            -nogndvcc
                do not create "GND" and "VCC" cells. (this will produce an error
                if the design contains constant nets. use "hilomap" to map to custom
                constant drivers first)
        
            -gndvccy
                create "GND" and "VCC" cells with "Y" outputs. (the default is
                "G" for "GND" and "P" for "VCC".)
        
            -attrprop
                create EDIF properties for cell attributes
        
            -keep
                create extra KEEP nets by allowing a cell to drive multiple nets.
        
            -pvector {par|bra|ang}
                sets the delimiting character for module port rename clauses to
                parentheses, square brackets, or angle brackets.
        
            -lsbidx
                use index 0 for the LSB bit of a net or port instead of MSB.
        
        Unfortunately there are different "flavors" of the EDIF file format. This
        command generates EDIF files for the Xilinx place&route tools. It might be
        necessary to make small modifications to this command when a different tool
        is targeted.
        
