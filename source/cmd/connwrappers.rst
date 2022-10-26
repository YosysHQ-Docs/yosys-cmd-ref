=====================================================
connwrappers - match width of input-output port pairs
=====================================================

.. only:: html

    :code:`yosys> help connwrappers`
    ----------------------------------------------------------------------------


    :code:`connwrappers [options] [selection]` ::

        Wrappers are used in coarse-grain synthesis to wrap cells with smaller ports
        in wrapper cells with a (larger) constant port size. I.e. the upper bits
        of the wrapper output are signed/unsigned bit extended. This command uses this
        knowledge to rewire the inputs of the driven cells to match the output of
        the driving cell.


    :code:`-signed <cell_type> <port_name> <width_param>`

    :code:`-unsigned <cell_type> <port_name> <width_param>` ::

            consider the specified signed/unsigned wrapper output


    :code:`-port <cell_type> <port_name> <width_param> <sign_param>` ::

            use the specified parameter to decide if signed or unsigned


    ::

        The options -signed, -unsigned, and -port can be specified multiple times.

.. only:: latex

    ::

        
            connwrappers [options] [selection]
        
        Wrappers are used in coarse-grain synthesis to wrap cells with smaller ports
        in wrapper cells with a (larger) constant port size. I.e. the upper bits
        of the wrapper output are signed/unsigned bit extended. This command uses this
        knowledge to rewire the inputs of the driven cells to match the output of
        the driving cell.
        
            -signed <cell_type> <port_name> <width_param>
            -unsigned <cell_type> <port_name> <width_param>
                consider the specified signed/unsigned wrapper output
        
            -port <cell_type> <port_name> <width_param> <sign_param>
                use the specified parameter to decide if signed or unsigned
        
        The options -signed, -unsigned, and -port can be specified multiple times.
        
