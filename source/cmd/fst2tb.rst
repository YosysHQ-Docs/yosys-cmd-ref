===========================================
fst2tb - generate testbench out of fst file
===========================================

.. only:: html

    :code:`yosys> help fst2tb`
    ----------------------------------------------------------------------------


    :code:`fst2tb [options] [top-level]` ::

        This command generates testbench for the circuit using the given top-level
        module and simulus signal from FST file


    :code:`-tb <name>` ::

            generated testbench name.
            files <name>.v and <name>.txt are created as result.


    :code:`-r <filename>` ::

            read simulation FST file


    :code:`-clock <portname>` ::

            name of top-level clock input


    :code:`-clockn <portname>` ::

            name of top-level clock input (inverse polarity)


    :code:`-scope <name>` ::

            scope of simulation top model


    :code:`-start <time>` ::

            start co-simulation in arbitary time (default 0)


    :code:`-stop <time>` ::

            stop co-simulation in arbitary time (default END)


    :code:`-n <integer>` ::

            number of clock cycles to simulate (default: 20)

.. only:: latex

    ::

        
            fst2tb [options] [top-level]
        
        This command generates testbench for the circuit using the given top-level
        module and simulus signal from FST file
        
            -tb <name>
                generated testbench name.
                files <name>.v and <name>.txt are created as result.
        
            -r <filename>
                read simulation FST file
        
            -clock <portname>
                name of top-level clock input
        
            -clockn <portname>
                name of top-level clock input (inverse polarity)
        
            -scope <name>
                scope of simulation top model
        
            -start <time>
                start co-simulation in arbitary time (default 0)
        
            -stop <time>
                stop co-simulation in arbitary time (default END)
        
            -n <integer>
                number of clock cycles to simulate (default: 20)
        
