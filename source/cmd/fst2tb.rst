===========================================
fst2tb - generate testbench out of fst file
===========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help fst2tb`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        fst2tb [options] [top-level]

    ::

        This command generates testbench for the circuit using the given top-level
        module and simulus signal from FST file


    .. code:: yoscrypt

        -tb <name>

    ::

            generated testbench name.
            files <name>.v and <name>.txt are created as result.


    .. code:: yoscrypt

        -r <filename>

    ::

            read simulation FST file


    .. code:: yoscrypt

        -clock <portname>

    ::

            name of top-level clock input


    .. code:: yoscrypt

        -clockn <portname>

    ::

            name of top-level clock input (inverse polarity)


    .. code:: yoscrypt

        -scope <name>

    ::

            scope of simulation top model


    .. code:: yoscrypt

        -start <time>

    ::

            start co-simulation in arbitary time (default 0)


    .. code:: yoscrypt

        -stop <time>

    ::

            stop co-simulation in arbitary time (default END)


    .. code:: yoscrypt

        -n <integer>

    ::

            number of clock cycles to simulate (default: 20)

.. raw:: latex

    \end{comment}

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
        
