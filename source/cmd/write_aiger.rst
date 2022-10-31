========================================
write_aiger - write design to AIGER file
========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_aiger`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_aiger [options] [filename]

    ::

        Write the current design to an AIGER file. The design must be flattened and
        must not contain any cell types except $_AND_, $_NOT_, simple FF types,
        $assert and $assume cells, and $initstate cells.

        $assert and $assume cells are converted to AIGER bad state properties and
        invariant constraints.


    .. code:: yoscrypt

        -ascii

    ::

            write ASCII version of AIGER format


    .. code:: yoscrypt

        -zinit

    ::

            convert FFs to zero-initialized FFs, adding additional inputs for
            uninitialized FFs.


    .. code:: yoscrypt

        -miter

    ::

            design outputs are AIGER bad state properties


    .. code:: yoscrypt

        -symbols

    ::

            include a symbol table in the generated AIGER file


    .. code:: yoscrypt

        -map <filename>

    ::

            write an extra file with port and latch symbols


    .. code:: yoscrypt

        -vmap <filename>

    ::

            like -map, but more verbose


    .. code:: yoscrypt

        -no-startoffset

    ::

            make indexes zero based, enable using map files with smt solvers.


    .. code:: yoscrypt

        -ywmap <filename>

    ::

            write a map file for conversion to and from yosys witness traces.


    .. code:: yoscrypt

        -I, -O, -B, -L

    ::

            If the design contains no input/output/assert/flip-flop then create one
            dummy input/output/bad_state-pin or latch to make the tools reading the
            AIGER file happy.

.. raw:: latex

    \end{comment}

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
        
