===========================================
synth_lattice - synthesis for Lattice FPGAs
===========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth_lattice`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth_lattice [options]

    ::

        This command runs synthesis for Lattice FPGAs (excluding iCE40 and Nexus).


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module


    .. code:: yoscrypt

        -family <family>

    ::

            run synthesis for the specified Lattice architecture
            generate the synthesis netlist for the specified family.
            supported values:
            - ecp5: ECP5
            - xo2: MachXO2
            - xo3: MachXO3L/LF
            - xo3d: MachXO3D


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

        -dff

    ::

            run 'abc'/'abc9' with -dff option


    .. code:: yoscrypt

        -retime

    ::

            run 'abc' with '-dff -D 1' options


    .. code:: yoscrypt

        -noccu2

    ::

            do not use CCU2 cells in output netlist


    .. code:: yoscrypt

        -nodffe

    ::

            do not use flipflops with CE in output netlist


    .. code:: yoscrypt

        -nobram

    ::

            do not use block RAM cells in output netlist


    .. code:: yoscrypt

        -nolutram

    ::

            do not use LUT RAM cells in output netlist


    .. code:: yoscrypt

        -nowidelut

    ::

            do not use PFU muxes to implement LUTs larger than LUT4s


    .. code:: yoscrypt

        -asyncprld

    ::

            use async PRLD mode to implement ALDFF (EXPERIMENTAL)


    .. code:: yoscrypt

        -abc2

    ::

            run two passes of 'abc' for slightly improved logic density


    .. code:: yoscrypt

        -abc9

    ::

            use new ABC9 flow (EXPERIMENTAL)


    .. code:: yoscrypt

        -iopad

    ::

            insert IO buffers


    .. code:: yoscrypt

        -nodsp

    ::

            do not map multipliers to MULT18X18D


    .. code:: yoscrypt

        -no-rw-check

    ::

            marks all recognized read ports as "return don't-care value on
            read/write collision" (same result as setting the no_rw_check
            attribute on all memories).



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib -specify +/lattice/cells_sim.v +/lattice/cells_bb.v
                hierarchy -check -top <top>

            coarse:
                proc
                flatten
                tribuf -logic
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm
                opt
                wreduce
                peepopt
                opt_clean
                share
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean
                alumacc
                opt
                memory -nomap [-no-rw-check]
                opt_clean

            map_ram:
                memory_libmap -lib +/lattice/lutrams.txt -lib +/lattice/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/lattice/lutrams_map.v -map +/lattice/brams_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                techmap -map +/techmap.v -map +/lattice/arith_map.v
                iopadmap -bits -outpad OB I:O -inpad IB O:I -toutpad OBZ ~T:I:O -tinoutpad BB ~T:O:I:B A:top    (only if '-iopad')
                attrmvcp -attr src -attr LOC t:OB %x:+[O] t:OBZ %x:+[O] t:BB %x:+[B]
                attrmvcp -attr src -attr LOC -driven t:IB %x:+[I]
                opt -fast
                abc -dff -D 1    (only if -retime)

            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 01 -cell $_DFF_?P?_ r -cell $_SDFF_?P?_ r [-cell $_DFFE_??_ 01 -cell $_DFFE_?P??_ r -cell $_SDFFE_?P??_ r] [-cell $_ALDFF_?P_ x -cell $_ALDFFE_?P?_ x] [-cell $_DLATCH_?_ x]    ($_ALDFF_*_ only if -asyncprld, $_DLATCH_* only if not -asyncprld, $_*DFFE_* only if not -nodffe)
                zinit -all w:* t:$_DFF_?_ t:$_DFFE_??_ t:$_SDFF*    (only if -abc9 and -dff)
                techmap -D NO_LUT -map +/lattice/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                lattice_gsr
                attrmvcp -copy -attr syn_useioff
                opt_clean

            map_luts:
                abc          (only if -abc2)
                techmap -map +/lattice/latches_map.v    (skip if -asyncprld)
                abc -dress -lut 4:7
                clean

            map_cells:
                techmap -map +/lattice/cells_map.v
                opt_lut_ins -tech lattice
                clean

            check:
                autoname
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

        
            synth_lattice [options]
        
        This command runs synthesis for Lattice FPGAs (excluding iCE40 and Nexus).
        
            -top <module>
                use the specified module as top module
        
            -family <family>
                run synthesis for the specified Lattice architecture
                generate the synthesis netlist for the specified family.
                supported values:
                - ecp5: ECP5
                - xo2: MachXO2
                - xo3: MachXO3L/LF
                - xo3d: MachXO3D
        
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
        
            -dff
                run 'abc'/'abc9' with -dff option
        
            -retime
                run 'abc' with '-dff -D 1' options
        
            -noccu2
                do not use CCU2 cells in output netlist
        
            -nodffe
                do not use flipflops with CE in output netlist
        
            -nobram
                do not use block RAM cells in output netlist
        
            -nolutram
                do not use LUT RAM cells in output netlist
        
            -nowidelut
                do not use PFU muxes to implement LUTs larger than LUT4s
        
            -asyncprld
                use async PRLD mode to implement ALDFF (EXPERIMENTAL)
        
            -abc2
                run two passes of 'abc' for slightly improved logic density
        
            -abc9
                use new ABC9 flow (EXPERIMENTAL)
        
            -iopad
                insert IO buffers
        
            -nodsp
                do not map multipliers to MULT18X18D
        
            -no-rw-check
                marks all recognized read ports as "return don't-care value on
                read/write collision" (same result as setting the no_rw_check
                attribute on all memories).
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -specify +/lattice/cells_sim.v +/lattice/cells_bb.v
                hierarchy -check -top <top>
        
            coarse:
                proc
                flatten
                tribuf -logic
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm
                opt
                wreduce
                peepopt
                opt_clean
                share
                techmap -map +/cmp2lut.v -D LUT_WIDTH=4
                opt_expr
                opt_clean
                alumacc
                opt
                memory -nomap [-no-rw-check]
                opt_clean
        
            map_ram:
                memory_libmap -lib +/lattice/lutrams.txt -lib +/lattice/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/lattice/lutrams_map.v -map +/lattice/brams_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                techmap -map +/techmap.v -map +/lattice/arith_map.v
                iopadmap -bits -outpad OB I:O -inpad IB O:I -toutpad OBZ ~T:I:O -tinoutpad BB ~T:O:I:B A:top    (only if '-iopad')
                attrmvcp -attr src -attr LOC t:OB %x:+[O] t:OBZ %x:+[O] t:BB %x:+[B]
                attrmvcp -attr src -attr LOC -driven t:IB %x:+[I]
                opt -fast
                abc -dff -D 1    (only if -retime)
        
            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 01 -cell $_DFF_?P?_ r -cell $_SDFF_?P?_ r [-cell $_DFFE_??_ 01 -cell $_DFFE_?P??_ r -cell $_SDFFE_?P??_ r] [-cell $_ALDFF_?P_ x -cell $_ALDFFE_?P?_ x] [-cell $_DLATCH_?_ x]    ($_ALDFF_*_ only if -asyncprld, $_DLATCH_* only if not -asyncprld, $_*DFFE_* only if not -nodffe)
                zinit -all w:* t:$_DFF_?_ t:$_DFFE_??_ t:$_SDFF*    (only if -abc9 and -dff)
                techmap -D NO_LUT -map +/lattice/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                lattice_gsr
                attrmvcp -copy -attr syn_useioff
                opt_clean
        
            map_luts:
                abc          (only if -abc2)
                techmap -map +/lattice/latches_map.v    (skip if -asyncprld)
                abc -dress -lut 4:7
                clean
        
            map_cells:
                techmap -map +/lattice/cells_map.v
                opt_lut_ins -tech lattice
                clean
        
            check:
                autoname
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            edif:
                write_edif <file-name>
        
            json:
                write_json <file-name>
        
