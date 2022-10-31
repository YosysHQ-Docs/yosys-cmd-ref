======================================================
extract - find subcircuits and replace them with cells
======================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help extract`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        extract -map <map_file> [options] [selection]

   
    .. code:: yoscrypt

        extract -mine <out_file> [options] [selection]

    ::

        This pass looks for subcircuits that are isomorphic to any of the modules
        in the given map file and replaces them with instances of this modules. The
        map file can be a Verilog source file (*.v) or an RTLIL source file (*.il).


    .. code:: yoscrypt

        -map <map_file>

    ::

            use the modules in this file as reference. This option can be used
            multiple times.


    .. code:: yoscrypt

        -map %<design-name>

    ::

            use the modules in this in-memory design as reference. This option can
            be used multiple times.


    .. code:: yoscrypt

        -verbose

    ::

            print debug output while analyzing


    .. code:: yoscrypt

        -constports

    ::

            also find instances with constant drivers. this may be much
            slower than the normal operation.


    .. code:: yoscrypt

        -nodefaultswaps

    ::

            normally builtin port swapping rules for internal cells are used per
            default. This turns that off, so e.g. 'a^b' does not match 'b^a'
            when this option is used.


    .. code:: yoscrypt

        -compat <needle_type> <haystack_type>

    ::

            Per default, the cells in the map file (needle) must have the
            type as the cells in the active design (haystack). This option
            can be used to register additional pairs of types that should
            match. This option can be used multiple times.


    .. code:: yoscrypt

        -swap <needle_type> <port1>,<port2>[,...]

    ::

            Register a set of swappable ports for a needle cell type.
            This option can be used multiple times.


    .. code:: yoscrypt

        -perm <needle_type> <port1>,<port2>[,...] <portA>,<portB>[,...]

    ::

            Register a valid permutation of swappable ports for a needle
            cell type. This option can be used multiple times.


    .. code:: yoscrypt

        -cell_attr <attribute_name>

    ::

            Attributes on cells with the given name must match.


    .. code:: yoscrypt

        -wire_attr <attribute_name>

    ::

            Attributes on wires with the given name must match.


    .. code:: yoscrypt

        -ignore_parameters

    ::

            Do not use parameters when matching cells.


    .. code:: yoscrypt

        -ignore_param <cell_type> <parameter_name>

    ::

            Do not use this parameter when matching cells.


    ::

        This pass does not operate on modules with unprocessed processes in it.
        (I.e. the 'proc' pass should be used first to convert processes to netlists.)

        This pass can also be used for mining for frequent subcircuits. In this mode
        the following options are to be used instead of the -map option.


    .. code:: yoscrypt

        -mine <out_file>

    ::

            mine for frequent subcircuits and write them to the given RTLIL file


    .. code:: yoscrypt

        -mine_cells_span <min> <max>

    ::

            only mine for subcircuits with the specified number of cells
            default value: 3 5


    .. code:: yoscrypt

        -mine_min_freq <num>

    ::

            only mine for subcircuits with at least the specified number of matches
            default value: 10


    .. code:: yoscrypt

        -mine_limit_matches_per_module <num>

    ::

            when calculating the number of matches for a subcircuit, don't count
            more than the specified number of matches per module


    .. code:: yoscrypt

        -mine_max_fanout <num>

    ::

            don't consider internal signals with more than <num> connections


    ::

        The modules in the map file may have the attribute 'extract_order' set to an
        integer value. Then this value is used to determine the order in which the pass
        tries to map the modules to the design (ascending, default value is 0).

        See 'help techmap' for a pass that does the opposite thing.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            extract -map <map_file> [options] [selection]
            extract -mine <out_file> [options] [selection]
        
        This pass looks for subcircuits that are isomorphic to any of the modules
        in the given map file and replaces them with instances of this modules. The
        map file can be a Verilog source file (*.v) or an RTLIL source file (*.il).
        
            -map <map_file>
                use the modules in this file as reference. This option can be used
                multiple times.
        
            -map %<design-name>
                use the modules in this in-memory design as reference. This option can
                be used multiple times.
        
            -verbose
                print debug output while analyzing
        
            -constports
                also find instances with constant drivers. this may be much
                slower than the normal operation.
        
            -nodefaultswaps
                normally builtin port swapping rules for internal cells are used per
                default. This turns that off, so e.g. 'a^b' does not match 'b^a'
                when this option is used.
        
            -compat <needle_type> <haystack_type>
                Per default, the cells in the map file (needle) must have the
                type as the cells in the active design (haystack). This option
                can be used to register additional pairs of types that should
                match. This option can be used multiple times.
        
            -swap <needle_type> <port1>,<port2>[,...]
                Register a set of swappable ports for a needle cell type.
                This option can be used multiple times.
        
            -perm <needle_type> <port1>,<port2>[,...] <portA>,<portB>[,...]
                Register a valid permutation of swappable ports for a needle
                cell type. This option can be used multiple times.
        
            -cell_attr <attribute_name>
                Attributes on cells with the given name must match.
        
            -wire_attr <attribute_name>
                Attributes on wires with the given name must match.
        
            -ignore_parameters
                Do not use parameters when matching cells.
        
            -ignore_param <cell_type> <parameter_name>
                Do not use this parameter when matching cells.
        
        This pass does not operate on modules with unprocessed processes in it.
        (I.e. the 'proc' pass should be used first to convert processes to netlists.)
        
        This pass can also be used for mining for frequent subcircuits. In this mode
        the following options are to be used instead of the -map option.
        
            -mine <out_file>
                mine for frequent subcircuits and write them to the given RTLIL file
        
            -mine_cells_span <min> <max>
                only mine for subcircuits with the specified number of cells
                default value: 3 5
        
            -mine_min_freq <num>
                only mine for subcircuits with at least the specified number of matches
                default value: 10
        
            -mine_limit_matches_per_module <num>
                when calculating the number of matches for a subcircuit, don't count
                more than the specified number of matches per module
        
            -mine_max_fanout <num>
                don't consider internal signals with more than <num> connections
        
        The modules in the map file may have the attribute 'extract_order' set to an
        integer value. Then this value is used to determine the order in which the pass
        tries to map the modules to the design (ascending, default value is 0).
        
        See 'help techmap' for a pass that does the opposite thing.
        
