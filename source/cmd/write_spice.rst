================================================
write_spice - write design to SPICE netlist file
================================================

.. only:: html

    :code:`yosys> help write_spice`
    ----------------------------------------------------------------------------


    :code:`write_spice [options] [filename]` ::

        Write the current design to an SPICE netlist file.


    :code:`-big_endian` ::

            generate multi-bit ports in MSB first order
            (default is LSB first)


    :code:`-neg net_name` ::

            set the net name for constant 0 (default: Vss)


    :code:`-pos net_name` ::

            set the net name for constant 1 (default: Vdd)


    :code:`-buf DC|subckt_name` ::

            set the name for jumper element (default: DC)
            (used to connect different nets)


    :code:`-nc_prefix` ::

            prefix for not-connected nets (default: _NC)


    :code:`-inames` ::

            include names of internal ($-prefixed) nets in outputs
            (default is to use net numbers instead)


    :code:`-top top_module` ::

            set the specified module as design top module

.. only:: latex

    ::

        
            write_spice [options] [filename]
        
        Write the current design to an SPICE netlist file.
        
            -big_endian
                generate multi-bit ports in MSB first order
                (default is LSB first)
        
            -neg net_name
                set the net name for constant 0 (default: Vss)
        
            -pos net_name
                set the net name for constant 1 (default: Vdd)
        
            -buf DC|subckt_name
                set the name for jumper element (default: DC)
                (used to connect different nets)
        
            -nc_prefix
                prefix for not-connected nets (default: _NC)
        
            -inames
                include names of internal ($-prefixed) nets in outputs
                (default is to use net numbers instead)
        
            -top top_module
                set the specified module as design top module
        
