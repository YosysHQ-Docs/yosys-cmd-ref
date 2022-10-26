========================================
write_aiger - write design to AIGER file
========================================

.. only:: html

    :code:`yosys> help write_aiger`
    ----------------------------------------------------------------------------


    :code:`write_aiger [options] [filename]` ::

        Write the current design to an AIGER file. The design must be flattened and
        must not contain any cell types except $_AND_, $_NOT_, simple FF types,
        $assert and $assume cells, and $initstate cells.

        $assert and $assume cells are converted to AIGER bad state properties and
        invariant constraints.


    :code:`-ascii` ::

            write ASCII version of AIGER format


    :code:`-zinit` ::

            convert FFs to zero-initialized FFs, adding additional inputs for
            uninitialized FFs.


    :code:`-miter` ::

            design outputs are AIGER bad state properties


    :code:`-symbols` ::

            include a symbol table in the generated AIGER file


    :code:`-map <filename>` ::

            write an extra file with port and latch symbols


    :code:`-vmap <filename>` ::

            like -map, but more verbose


    :code:`-no-startoffset` ::

            make indexes zero based, enable using map files with smt solvers.


    :code:`-ywmap <filename>` ::

            write a map file for conversion to and from yosys witness traces.


    :code:`-I, -O, -B, -L` ::

            If the design contains no input/output/assert/flip-flop then create one
            dummy input/output/bad_state-pin or latch to make the tools reading the
            AIGER file happy.

.. only:: latex

    ::

        
            write_aiger [options] [filename]
        
        Write the current design to an AIGER file. The design must be flattened and
        must not contain any cell types except $_AND_, $_NOT_, simple FF types,
        $assert and $assume cells, and $initstate cells.
        
        $assert and $assume cells are converted to AIGER bad state properties and
        invariant constraints.
        
            -ascii
                write ASCII version of AIGER format
        
            -zinit
                convert FFs to zero-initialized FFs, adding additional inputs for
                uninitialized FFs.
        
            -miter
                design outputs are AIGER bad state properties
        
            -symbols
                include a symbol table in the generated AIGER file
        
            -map <filename>
                write an extra file with port and latch symbols
        
            -vmap <filename>
                like -map, but more verbose
        
            -no-startoffset
                make indexes zero based, enable using map files with smt solvers.
        
            -ywmap <filename>
                write a map file for conversion to and from yosys witness traces.
        
            -I, -O, -B, -L
                If the design contains no input/output/assert/flip-flop then create one
                dummy input/output/bad_state-pin or latch to make the tools reading the
                AIGER file happy.
        
