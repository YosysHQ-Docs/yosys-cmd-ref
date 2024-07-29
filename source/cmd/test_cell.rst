================================================================
test_cell - automatically test the implementation of a cell type
================================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: test_cell
    :title: automatically test the implementation of a cell type



    .. code:: yoscrypt

        test_cell [options] {cell-types}

    ::

        Tests the internal implementation of the given cell type (for example '$add')
        by comparing SAT solver, EVAL and TECHMAP implementations of the cell types..

        Run with 'all' instead of a cell type to run the test on all supported
        cell types. Use for example 'all /$add' for all cell types except $add.


    .. code:: yoscrypt

        -n {integer}

    ::

            create this number of cell instances and test them (default = 100).


    .. code:: yoscrypt

        -s {positive_integer}

    ::

            use this value as rng seed value (default = unix time).


    .. code:: yoscrypt

        -f {rtlil_file}

    ::

            don't generate circuits. instead load the specified RTLIL file.


    .. code:: yoscrypt

        -w {filename_prefix}

    ::

            don't test anything. just generate the circuits and write them
            to RTLIL files with the specified prefix


    .. code:: yoscrypt

        -map {filename}

    ::

            pass this option to techmap.


    .. code:: yoscrypt

        -simlib

    ::

            use "techmap -D SIMLIB_NOCHECKS -map +/simlib.v -max_iter 2 -autoproc"


    .. code:: yoscrypt

        -aigmap

    ::

            instead of calling "techmap", call "aigmap"


    .. code:: yoscrypt

        -muxdiv

    ::

            when creating test benches with dividers, create an additional mux
            to mask out the division-by-zero case


    .. code:: yoscrypt

        -script {script_file}

    ::

            instead of calling "techmap", call "script {script_file}".


    .. code:: yoscrypt

        -const

    ::

            set some input bits to random constant values


    .. code:: yoscrypt

        -nosat

    ::

            do not check SAT model or run SAT equivalence checking


    .. code:: yoscrypt

        -noeval

    ::

            do not check const-eval models


    .. code:: yoscrypt

        -noopt

    ::

            do not opt tecchmapped design


    .. code:: yoscrypt

        -edges

    ::

            test cell edges db creator against sat-based implementation


    .. code:: yoscrypt

        -v

    ::

            print additional debug information to the console


    .. code:: yoscrypt

        -vlog {filename}

    ::

            create a Verilog test bench to test simlib and write_verilog

    ::

        -bloat {factor}
            increase cell size limits b{factor} times where possible

    ::

        -check_cost
            check if the estimated cell cost is a valid upper bound for
            the techmapped cell count 

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            test_cell [options] {cell-types}
        
        Tests the internal implementation of the given cell type (for example '$add')
        by comparing SAT solver, EVAL and TECHMAP implementations of the cell types..
        
        Run with 'all' instead of a cell type to run the test on all supported
        cell types. Use for example 'all /$add' for all cell types except $add.
        
            -n {integer}
                create this number of cell instances and test them (default = 100).
        
            -s {positive_integer}
                use this value as rng seed value (default = unix time).
        
            -f {rtlil_file}
                don't generate circuits. instead load the specified RTLIL file.
        
            -w {filename_prefix}
                don't test anything. just generate the circuits and write them
                to RTLIL files with the specified prefix
        
            -map {filename}
                pass this option to techmap.
        
            -simlib
                use "techmap -D SIMLIB_NOCHECKS -map +/simlib.v -max_iter 2 -autoproc"
        
            -aigmap
                instead of calling "techmap", call "aigmap"
        
            -muxdiv
                when creating test benches with dividers, create an additional mux
                to mask out the division-by-zero case
        
            -script {script_file}
                instead of calling "techmap", call "script {script_file}".
        
            -const
                set some input bits to random constant values
        
            -nosat
                do not check SAT model or run SAT equivalence checking
        
            -noeval
                do not check const-eval models
        
            -noopt
                do not opt tecchmapped design
        
            -edges
                test cell edges db creator against sat-based implementation
        
            -v
                print additional debug information to the console
        
            -vlog {filename}
                create a Verilog test bench to test simlib and write_verilog
            -bloat {factor}
                increase cell size limits b{factor} times where possible
            -check_cost
                check if the estimated cell cost is a valid upper bound for
                the techmapped cell count 
        
