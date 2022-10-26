===============================================
synth_nexus - synthesis for Lattice Nexus FPGAs
===============================================

.. only:: html

    :code:`yosys> help synth_nexus`
    ----------------------------------------------------------------------------


    :code:`synth_nexus [options]` ::

        This command runs synthesis for Lattice Nexus FPGAs.


    :code:`-top <module>` ::

            use the specified module as top module


    :code:`-family <device>` ::

            run synthesis for the specified Nexus device
            supported values: lifcl, lfd2nx


    :code:`-json <file>` ::

            write the design to the specified JSON file. writing of an output file
            is omitted if this parameter is not specified.


    :code:`-vm <file>` ::

            write the design to the specified structural Verilog file. writing of
            an output file is omitted if this parameter is not specified.


    :code:`-run <from_label>:<to_label>` ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    :code:`-noflatten` ::

            do not flatten design before synthesis


    :code:`-dff` ::

            run 'abc'/'abc9' with -dff option


    :code:`-retime` ::

            run 'abc' with '-dff -D 1' options


    :code:`-noccu2` ::

            do not use CCU2 cells in output netlist


    :code:`-nodffe` ::

            do not use flipflops with CE in output netlist


    :code:`-nolram` ::

            do not use large RAM cells in output netlist
            note that large RAM must be explicitly requested with a (* lram *)
            attribute on the memory.


    :code:`-nobram` ::

            do not use block RAM cells in output netlist


    :code:`-nolutram` ::

            do not use LUT RAM cells in output netlist


    :code:`-nowidelut` ::

            do not use PFU muxes to implement LUTs larger than LUT4s


    :code:`-noiopad` ::

            do not insert IO buffers


    :code:`-nodsp` ::

            do not infer DSP multipliers


    :code:`-abc9` ::

            use new ABC9 flow (EXPERIMENTAL)


    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib -specify +/nexus/cells_sim.v +/nexus/cells_xtra.v
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
                techmap -map +/mul2dsp.v [...]    (unless -nodsp)
                techmap -map +/nexus/dsp_map.v    (unless -nodsp)
                alumacc
                opt
                memory -nomap
                opt_clean

            map_ram:
                memory_libmap -lib +/nexus/lutrams.txt -lib +/nexus/brams.txt -lib +/nexus/lrams.txt -no-auto-huge [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/nexus/lutrams_map.v -map +/nexus/brams_map.v -map +/nexus/lrams_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                techmap -map +/techmap.v -map +/nexus/arith_map.v
                iopadmap -bits -outpad OB I:O -inpad IB O:I -toutpad OBZ ~T:I:O -tinoutpad BB ~T:O:I:B A:top    (skip if '-noiopad')
                opt -fast
                abc -dff -D 1    (only if -retime)

            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_P_ 01 -cell $_DFF_PP?_ r -cell $_SDFF_PP?_ r -cell $_DLATCH_?_ x [-cell $_DFFE_PP_ 01 -cell $_DFFE_PP?P_ r -cell $_SDFFE_PP?P_ r]    ($_*DFFE_* only if not -nodffe)
                zinit -all w:* t:$_DFF_?_ t:$_DFFE_??_ t:$_SDFF*    (only if -abc9 and -dff
                techmap -D NO_LUT -map +/nexus/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                attrmvcp -copy -attr syn_useioff
                opt_clean

            map_luts:
                techmap -map +/nexus/latches_map.v
                abc -dress -lut 4:5
                clean

            map_cells:
                techmap -map +/nexus/cells_map.v
                setundef -zero
                hilomap -singleton -hicell VHI Z -locell VLO Z
                clean

            check:
                autoname
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            json:
                write_json <file-name>

            vm:
                write_verilog <file-name>

.. only:: latex

    ::

        
            synth_nexus [options]
        
        This command runs synthesis for Lattice Nexus FPGAs.
        
            -top <module>
                use the specified module as top module
        
            -family <device>
                run synthesis for the specified Nexus device
                supported values: lifcl, lfd2nx
        
            -json <file>
                write the design to the specified JSON file. writing of an output file
                is omitted if this parameter is not specified.
        
            -vm <file>
                write the design to the specified structural Verilog file. writing of
                an output file is omitted if this parameter is not specified.
        
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
        
            -nolram
                do not use large RAM cells in output netlist
                note that large RAM must be explicitly requested with a (* lram *)
                attribute on the memory.
        
            -nobram
                do not use block RAM cells in output netlist
        
            -nolutram
                do not use LUT RAM cells in output netlist
        
            -nowidelut
                do not use PFU muxes to implement LUTs larger than LUT4s
        
            -noiopad
                do not insert IO buffers
        
            -nodsp
                do not infer DSP multipliers
        
            -abc9
                use new ABC9 flow (EXPERIMENTAL)
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -specify +/nexus/cells_sim.v +/nexus/cells_xtra.v
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
                techmap -map +/mul2dsp.v [...]    (unless -nodsp)
                techmap -map +/nexus/dsp_map.v    (unless -nodsp)
                alumacc
                opt
                memory -nomap
                opt_clean
        
            map_ram:
                memory_libmap -lib +/nexus/lutrams.txt -lib +/nexus/brams.txt -lib +/nexus/lrams.txt -no-auto-huge [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/nexus/lutrams_map.v -map +/nexus/brams_map.v -map +/nexus/lrams_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                techmap -map +/techmap.v -map +/nexus/arith_map.v
                iopadmap -bits -outpad OB I:O -inpad IB O:I -toutpad OBZ ~T:I:O -tinoutpad BB ~T:O:I:B A:top    (skip if '-noiopad')
                opt -fast
                abc -dff -D 1    (only if -retime)
        
            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_P_ 01 -cell $_DFF_PP?_ r -cell $_SDFF_PP?_ r -cell $_DLATCH_?_ x [-cell $_DFFE_PP_ 01 -cell $_DFFE_PP?P_ r -cell $_SDFFE_PP?P_ r]    ($_*DFFE_* only if not -nodffe)
                zinit -all w:* t:$_DFF_?_ t:$_DFFE_??_ t:$_SDFF*    (only if -abc9 and -dff
                techmap -D NO_LUT -map +/nexus/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                attrmvcp -copy -attr syn_useioff
                opt_clean
        
            map_luts:
                techmap -map +/nexus/latches_map.v
                abc -dress -lut 4:5
                clean
        
            map_cells:
                techmap -map +/nexus/cells_map.v
                setundef -zero
                hilomap -singleton -hicell VHI Z -locell VLO Z
                clean
        
            check:
                autoname
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            json:
                write_json <file-name>
        
            vm:
                write_verilog <file-name>
        
