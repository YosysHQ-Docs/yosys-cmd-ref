===========================================
synth_anlogic - synthesis for Anlogic FPGAs
===========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_anlogic
    :title: synthesis for Anlogic FPGAs



    .. code:: yoscrypt

        synth_anlogic [options]

    ::

        This command runs synthesis for Anlogic FPGAs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module


    .. code:: yoscrypt

        -edif <file>

    ::

            write the design to the specified EDIF file. writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -json <file>

    ::

            write the design to the specified JSON file. writing of an output file
            is omitted if this parameter is not specified.


    .. code:: yoscrypt

        -run <from_label>:<to_label>

    ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -noflatten

    ::

            do not flatten design before synthesis


    .. code:: yoscrypt

        -retime

    ::

            run 'abc' with '-dff -D 1' options


    .. code:: yoscrypt

        -nolutram

    ::

            do not use EG_LOGIC_DRAM16X4 cells in output netlist


    .. code:: yoscrypt

        -nobram

    ::

            do not use EG_PHY_BRAM or EG_PHY_BRAM32K cells in output netlist



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib +/anlogic/cells_sim.v +/anlogic/eagle_bb.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout

            coarse:
                synth -run coarse

            map_ram:
                memory_libmap -lib +/anlogic/lutrams.txt -lib +/anlogic/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/anlogic/lutrams_map.v -map +/anlogic/brams_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                techmap -map +/techmap.v -map +/anlogic/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)

            map_ffs:
                dfflegalize -cell $_DFFE_P??P_ r -cell $_SDFFE_P??P_ r -cell $_DLATCH_N??_ r
                techmap -D NO_LUT -map +/anlogic/cells_map.v
                opt_expr -mux_undef
                simplemap

            map_luts:
                abc -lut 4:6
                clean

            map_cells:
                techmap -map +/anlogic/cells_map.v
                clean

            map_anlogic:
                anlogic_fixcarry
                anlogic_eqn

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            edif:
                write_edif <file-name>

            json:
                write_json <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_anlogic [options]
        
        This command runs synthesis for Anlogic FPGAs.
        
            -top <module>
                use the specified module as top module
        
            -edif <file>
                write the design to the specified EDIF file. writing of an output file
                is omitted if this parameter is not specified.
        
            -json <file>
                write the design to the specified JSON file. writing of an output file
                is omitted if this parameter is not specified.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -noflatten
                do not flatten design before synthesis
        
            -retime
                run 'abc' with '-dff -D 1' options
        
            -nolutram
                do not use EG_LOGIC_DRAM16X4 cells in output netlist
        
            -nobram
                do not use EG_PHY_BRAM or EG_PHY_BRAM32K cells in output netlist
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib +/anlogic/cells_sim.v +/anlogic/eagle_bb.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout
        
            coarse:
                synth -run coarse
        
            map_ram:
                memory_libmap -lib +/anlogic/lutrams.txt -lib +/anlogic/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/anlogic/lutrams_map.v -map +/anlogic/brams_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                techmap -map +/techmap.v -map +/anlogic/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
        
            map_ffs:
                dfflegalize -cell $_DFFE_P??P_ r -cell $_SDFFE_P??P_ r -cell $_DLATCH_N??_ r
                techmap -D NO_LUT -map +/anlogic/cells_map.v
                opt_expr -mux_undef
                simplemap
        
            map_luts:
                abc -lut 4:6
                clean
        
            map_cells:
                techmap -map +/anlogic/cells_map.v
                clean
        
            map_anlogic:
                anlogic_fixcarry
                anlogic_eqn
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            edif:
                write_edif <file-name>
        
            json:
                write_json <file-name>
        
