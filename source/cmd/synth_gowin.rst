=======================================
synth_gowin - synthesis for Gowin FPGAs
=======================================

.. only:: html

    :code:`yosys> help synth_gowin`
    ----------------------------------------------------------------------------


    :code:`synth_gowin [options]` ::

        This command runs synthesis for Gowin FPGAs. This work is experimental.


    :code:`-top <module>` ::

            use the specified module as top module (default='top')


    :code:`-vout <file>` ::

            write the design to the specified Verilog netlist file. writing of an
            output file is omitted if this parameter is not specified.


    :code:`-json <file>` ::

            write the design to the specified JSON netlist file. writing of an
            output file is omitted if this parameter is not specified.
            This disables features not yet supported by nexpnr-gowin.


    :code:`-run <from_label>:<to_label>` ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    :code:`-nodffe` ::

            do not use flipflops with CE in output netlist


    :code:`-nobram` ::

            do not use BRAM cells in output netlist


    :code:`-nolutram` ::

            do not use distributed RAM cells in output netlist


    :code:`-noflatten` ::

            do not flatten design before synthesis


    :code:`-retime` ::

            run 'abc' with '-dff -D 1' options


    :code:`-nowidelut` ::

            do not use muxes to implement LUTs larger than LUT4s


    :code:`-noiopads` ::

            do not emit IOB at top level ports


    :code:`-noalu` ::

            do not use ALU cells


    :code:`-abc9` ::

            use new ABC9 flow (EXPERIMENTAL)


    :code:`-no-rw-check` ::

            marks all recognized read ports as "return don't-care value on
            read/write collision" (same result as setting the no_rw_check
            attribute on all memories).



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -specify -lib +/gowin/cells_sim.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout

            coarse:
                synth -run coarse [-no-rw-check]

            map_ram:
                memory_libmap -lib +/gowin/lutrams.txt -lib +/gowin/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/gowin/lutrams_map.v -map +/gowin/brams_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                techmap -map +/techmap.v -map +/gowin/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
                iopadmap -bits -inpad IBUF O:I -outpad OBUF I:O -toutpad TBUF ~OEN:I:O -tinoutpad IOBUF ~OEN:O:I:IO    (unless -noiopads)

            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 0 -cell $_DFFE_?P_ 0 -cell $_SDFF_?P?_ r -cell $_SDFFE_?P?P_ r -cell $_DFF_?P?_ r -cell $_DFFE_?P?P_ r
                techmap -map +/gowin/cells_map.v
                opt_expr -mux_undef
                simplemap

            map_luts:
                abc -lut 4:8
                clean

            map_cells:
                techmap -map +/gowin/cells_map.v
                opt_lut_ins -tech gowin
                setundef -undriven -params -zero
                hilomap -singleton -hicell VCC V -locell GND G
                splitnets -ports    (only if -vout used)
                clean
                autoname

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            vout:
                write_verilog -simple-lhs -decimal -attr2comment -defparam -renameprefix gen <file-name>
                write_json <file-name>

.. only:: latex

    ::

        
            synth_gowin [options]
        
        This command runs synthesis for Gowin FPGAs. This work is experimental.
        
            -top <module>
                use the specified module as top module (default='top')
        
            -vout <file>
                write the design to the specified Verilog netlist file. writing of an
                output file is omitted if this parameter is not specified.
        
            -json <file>
                write the design to the specified JSON netlist file. writing of an
                output file is omitted if this parameter is not specified.
                This disables features not yet supported by nexpnr-gowin.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -nodffe
                do not use flipflops with CE in output netlist
        
            -nobram
                do not use BRAM cells in output netlist
        
            -nolutram
                do not use distributed RAM cells in output netlist
        
            -noflatten
                do not flatten design before synthesis
        
            -retime
                run 'abc' with '-dff -D 1' options
        
            -nowidelut
                do not use muxes to implement LUTs larger than LUT4s
        
            -noiopads
                do not emit IOB at top level ports
        
            -noalu
                do not use ALU cells
        
            -abc9
                use new ABC9 flow (EXPERIMENTAL)
        
            -no-rw-check
                marks all recognized read ports as "return don't-care value on
                read/write collision" (same result as setting the no_rw_check
                attribute on all memories).
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -specify -lib +/gowin/cells_sim.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout
        
            coarse:
                synth -run coarse [-no-rw-check]
        
            map_ram:
                memory_libmap -lib +/gowin/lutrams.txt -lib +/gowin/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/gowin/lutrams_map.v -map +/gowin/brams_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                techmap -map +/techmap.v -map +/gowin/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
                iopadmap -bits -inpad IBUF O:I -outpad OBUF I:O -toutpad TBUF ~OEN:I:O -tinoutpad IOBUF ~OEN:O:I:IO    (unless -noiopads)
        
            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 0 -cell $_DFFE_?P_ 0 -cell $_SDFF_?P?_ r -cell $_SDFFE_?P?P_ r -cell $_DFF_?P?_ r -cell $_DFFE_?P?P_ r
                techmap -map +/gowin/cells_map.v
                opt_expr -mux_undef
                simplemap
        
            map_luts:
                abc -lut 4:8
                clean
        
            map_cells:
                techmap -map +/gowin/cells_map.v
                opt_lut_ins -tech gowin
                setundef -undriven -params -zero
                hilomap -singleton -hicell VCC V -locell GND G
                splitnets -ports    (only if -vout used)
                clean
                autoname
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            vout:
                write_verilog -simple-lhs -decimal -attr2comment -defparam -renameprefix gen <file-name>
                write_json <file-name>
        
