==========================
sim - simulate the circuit
==========================

.. only:: html

    :code:`yosys> help sim`
    ----------------------------------------------------------------------------


    :code:`sim [options] [top-level]` ::

        This command simulates the circuit using the given top-level module.


    :code:`-vcd <filename>` ::

            write the simulation results to the given VCD file


    :code:`-fst <filename>` ::

            write the simulation results to the given FST file


    :code:`-aiw <filename>` ::

            write the simulation results to an AIGER witness file
            (requires a *.aim file via -map)


    :code:`-hdlname` ::

            use the hdlname attribute when writing simulation results
            (preserves hierarchy in a flattened design)


    :code:`-x` ::

            ignore constant x outputs in simulation file.


    :code:`-date` ::

            include date and full version info in output.


    :code:`-clock <portname>` ::

            name of top-level clock input


    :code:`-clockn <portname>` ::

            name of top-level clock input (inverse polarity)


    :code:`-multiclock` ::

            mark that witness file is multiclock.


    :code:`-reset <portname>` ::

            name of top-level reset input (active high)


    :code:`-resetn <portname>` ::

            name of top-level inverted reset input (active low)


    :code:`-rstlen <integer>` ::

            number of cycles reset should stay active (default: 1)


    :code:`-zinit` ::

            zero-initialize all uninitialized regs and memories


    :code:`-timescale <string>` ::

            include the specified timescale declaration in the vcd


    :code:`-n <integer>` ::

            number of clock cycles to simulate (default: 20)


    :code:`-a` ::

            use all nets in VCD/FST operations, not just those with public names


    :code:`-w` ::

            writeback mode: use final simulation state as new init state


    :code:`-r` ::

            read simulation results file
                File formats supported: FST, VCD, AIW and WIT
                VCD support requires vcd2fst external tool to be present


    :code:`-map <filename>` ::

            read file with port and latch symbols, needed for AIGER witness input


    :code:`-scope <name>` ::

            scope of simulation top model


    :code:`-at <time>` ::

            sets start and stop time


    :code:`-start <time>` ::

            start co-simulation in arbitary time (default 0)


    :code:`-stop <time>` ::

            stop co-simulation in arbitary time (default END)


    :code:`-sim` ::

            simulation with stimulus from FST (default)


    :code:`-sim-cmp` ::

            co-simulation expect exact match


    :code:`-sim-gold` ::

            co-simulation, x in simulation can match any value in FST


    :code:`-sim-gate` ::

            co-simulation, x in FST can match any value in simulation


    :code:`-q` ::

            disable per-cycle/sample log message


    :code:`-d` ::

            enable debug output

.. only:: latex

    ::

        
            sim [options] [top-level]
        
        This command simulates the circuit using the given top-level module.
        
            -vcd <filename>
                write the simulation results to the given VCD file
        
            -fst <filename>
                write the simulation results to the given FST file
        
            -aiw <filename>
                write the simulation results to an AIGER witness file
                (requires a *.aim file via -map)
        
            -hdlname
                use the hdlname attribute when writing simulation results
                (preserves hierarchy in a flattened design)
        
            -x
                ignore constant x outputs in simulation file.
        
            -date
                include date and full version info in output.
        
            -clock <portname>
                name of top-level clock input
        
            -clockn <portname>
                name of top-level clock input (inverse polarity)
        
            -multiclock
                mark that witness file is multiclock.
        
            -reset <portname>
                name of top-level reset input (active high)
        
            -resetn <portname>
                name of top-level inverted reset input (active low)
        
            -rstlen <integer>
                number of cycles reset should stay active (default: 1)
        
            -zinit
                zero-initialize all uninitialized regs and memories
        
            -timescale <string>
                include the specified timescale declaration in the vcd
        
            -n <integer>
                number of clock cycles to simulate (default: 20)
        
            -a
                use all nets in VCD/FST operations, not just those with public names
        
            -w
                writeback mode: use final simulation state as new init state
        
            -r
                read simulation results file
                    File formats supported: FST, VCD, AIW and WIT
                    VCD support requires vcd2fst external tool to be present
        
            -map <filename>
                read file with port and latch symbols, needed for AIGER witness input
        
            -scope <name>
                scope of simulation top model
        
            -at <time>
                sets start and stop time
        
            -start <time>
                start co-simulation in arbitary time (default 0)
        
            -stop <time>
                stop co-simulation in arbitary time (default END)
        
            -sim
                simulation with stimulus from FST (default)
        
            -sim-cmp
                co-simulation expect exact match
        
            -sim-gold
                co-simulation, x in simulation can match any value in FST
        
            -sim-gate
                co-simulation, x in FST can match any value in simulation
        
            -q
                disable per-cycle/sample log message
        
            -d
                enable debug output
        
