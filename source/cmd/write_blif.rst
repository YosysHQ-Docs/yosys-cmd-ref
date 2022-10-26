======================================
write_blif - write design to BLIF file
======================================

.. only:: html

    :code:`yosys> help write_blif`
    ----------------------------------------------------------------------------


    :code:`write_blif [options] [filename]` ::

        Write the current design to an BLIF file.


    :code:`-top top_module` ::

            set the specified module as design top module


    :code:`-buf <cell-type> <in-port> <out-port>` ::

            use cells of type <cell-type> with the specified port names for buffers


    :code:`-unbuf <cell-type> <in-port> <out-port>` ::

            replace buffer cells with the specified name and port names with
            a .names statement that models a buffer


    :code:`-true <cell-type> <out-port>`

    :code:`-false <cell-type> <out-port>`

    :code:`-undef <cell-type> <out-port>` ::

            use the specified cell types to drive nets that are constant 1, 0, or
            undefined. when '-' is used as <cell-type>, then <out-port> specifies
            the wire name to be used for the constant signal and no cell driving
            that wire is generated. when '+' is used as <cell-type>, then <out-port>
            specifies the wire name to be used for the constant signal and a .names
            statement is generated to drive the wire.


    :code:`-noalias` ::

            if a net name is aliasing another net name, then by default a net
            without fanout is created that is driven by the other net. This option
            suppresses the generation of this nets without fanout.


    ::

        The following options can be useful when the generated file is not going to be
        read by a BLIF parser but a custom tool. It is recommended to not name the
        output file *.blif when any of this options is used.


    :code:`-icells` ::

            do not translate Yosys's internal gates to generic BLIF logic
            functions. Instead create .subckt or .gate lines for all cells.


    :code:`-gates` ::

            print .gate instead of .subckt lines for all cells that are not
            instantiations of other modules from this design.


    :code:`-conn` ::

            do not generate buffers for connected wires. instead use the
            non-standard .conn statement.


    :code:`-attr` ::

            use the non-standard .attr statement to write cell attributes


    :code:`-param` ::

            use the non-standard .param statement to write cell parameters


    :code:`-cname` ::

            use the non-standard .cname statement to write cell names


    :code:`-iname, -iattr` ::

            enable -cname and -attr functionality for .names statements
            (the .cname and .attr statements will be included in the BLIF
            output after the truth table for the .names statement)


    :code:`-blackbox` ::

            write blackbox cells with .blackbox statement.


    :code:`-impltf` ::

            do not write definitions for the $true, $false and $undef wires.

.. only:: latex

    ::

        
            write_blif [options] [filename]
        
        Write the current design to an BLIF file.
        
            -top top_module
                set the specified module as design top module
        
            -buf <cell-type> <in-port> <out-port>
                use cells of type <cell-type> with the specified port names for buffers
        
            -unbuf <cell-type> <in-port> <out-port>
                replace buffer cells with the specified name and port names with
                a .names statement that models a buffer
        
            -true <cell-type> <out-port>
            -false <cell-type> <out-port>
            -undef <cell-type> <out-port>
                use the specified cell types to drive nets that are constant 1, 0, or
                undefined. when '-' is used as <cell-type>, then <out-port> specifies
                the wire name to be used for the constant signal and no cell driving
                that wire is generated. when '+' is used as <cell-type>, then <out-port>
                specifies the wire name to be used for the constant signal and a .names
                statement is generated to drive the wire.
        
            -noalias
                if a net name is aliasing another net name, then by default a net
                without fanout is created that is driven by the other net. This option
                suppresses the generation of this nets without fanout.
        
        The following options can be useful when the generated file is not going to be
        read by a BLIF parser but a custom tool. It is recommended to not name the
        output file *.blif when any of this options is used.
        
            -icells
                do not translate Yosys's internal gates to generic BLIF logic
                functions. Instead create .subckt or .gate lines for all cells.
        
            -gates
                print .gate instead of .subckt lines for all cells that are not
                instantiations of other modules from this design.
        
            -conn
                do not generate buffers for connected wires. instead use the
                non-standard .conn statement.
        
            -attr
                use the non-standard .attr statement to write cell attributes
        
            -param
                use the non-standard .param statement to write cell parameters
        
            -cname
                use the non-standard .cname statement to write cell names
        
            -iname, -iattr
                enable -cname and -attr functionality for .names statements
                (the .cname and .attr statements will be included in the BLIF
                output after the truth table for the .names statement)
        
            -blackbox
                write blackbox cells with .blackbox statement.
        
            -impltf
                do not write definitions for the $true, $false and $undef wires.
        
