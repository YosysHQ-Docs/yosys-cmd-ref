=======================================
splice - create explicit splicing cells
=======================================

.. only:: html

    :code:`yosys> help splice`
    ----------------------------------------------------------------------------


    :code:`splice [options] [selection]` ::

        This command adds $slice and $concat cells to the design to make the splicing
        of multi-bit signals explicit. This for example is useful for coarse grain
        synthesis, where dedicated hardware is needed to splice signals.


    :code:`-sel_by_cell` ::

            only select the cell ports to rewire by the cell. if the selection
            contains a cell, than all cell inputs are rewired, if necessary.


    :code:`-sel_by_wire` ::

            only select the cell ports to rewire by the wire. if the selection
            contains a wire, than all cell ports driven by this wire are wired,
            if necessary.


    :code:`-sel_any_bit` ::

            it is sufficient if the driver of any bit of a cell port is selected.
            by default all bits must be selected.


    :code:`-wires` ::

            also add $slice and $concat cells to drive otherwise unused wires.


    :code:`-no_outputs` ::

            do not rewire selected module outputs.


    :code:`-port <name>` ::

            only rewire cell ports with the specified name. can be used multiple
            times. implies -no_output.


    :code:`-no_port <name>` ::

            do not rewire cell ports with the specified name. can be used multiple
            times. can not be combined with -port <name>.


    ::

        By default selected output wires and all cell ports of selected cells driven
        by selected wires are rewired.

.. only:: latex

    ::

        
            splice [options] [selection]
        
        This command adds $slice and $concat cells to the design to make the splicing
        of multi-bit signals explicit. This for example is useful for coarse grain
        synthesis, where dedicated hardware is needed to splice signals.
        
            -sel_by_cell
                only select the cell ports to rewire by the cell. if the selection
                contains a cell, than all cell inputs are rewired, if necessary.
        
            -sel_by_wire
                only select the cell ports to rewire by the wire. if the selection
                contains a wire, than all cell ports driven by this wire are wired,
                if necessary.
        
            -sel_any_bit
                it is sufficient if the driver of any bit of a cell port is selected.
                by default all bits must be selected.
        
            -wires
                also add $slice and $concat cells to drive otherwise unused wires.
        
            -no_outputs
                do not rewire selected module outputs.
        
            -port <name>
                only rewire cell ports with the specified name. can be used multiple
                times. implies -no_output.
        
            -no_port <name>
                do not rewire cell ports with the specified name. can be used multiple
                times. can not be combined with -port <name>.
        
        By default selected output wires and all cell ports of selected cells driven
        by selected wires are rewired.
        
