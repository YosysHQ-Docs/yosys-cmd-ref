=====================================
synth_ecp5 - synthesis for ECP5 FPGAs
=====================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth_ecp5`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth_ecp5 [options]

    ::

        This command runs synthesis for ECP5 FPGAs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module


    .. code:: yoscrypt

        -blif <file>

    ::

            write the design to the specified BLIF file. writing of an output file
            is omitted if this parameter is not specified.


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

        -vpr

    ::

            generate an output netlist (and BLIF file) suitable for VPR
            (this feature is experimental and incomplete)


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
                read_verilog -lib -specify +/ecp5/cells_sim.v +/ecp5/cells_bb.v
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
                techmap -map +/mul2dsp.v -map +/ecp5/dsp_map.v -D DSP_A_MAXWIDTH=18 -D DSP_B_MAXWIDTH=18  -D DSP_A_MINWIDTH=2 -D DSP_B_MINWIDTH=2  -D DSP_NAME=$__MUL18X18    (unless -nodsp)
                chtype -set $mul t:$__soft_mul    (unless -nodsp)
                alumacc
                opt
                memory -nomap [-no-rw-check]
                opt_clean

            map_ram:
                memory_libmap -lib +/ecp5/lutrams.txt -lib +/ecp5/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/ecp5/lutrams_map.v -map +/ecp5/brams_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                techmap -map +/techmap.v -map +/ecp5/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)

            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 01 -cell $_DFF_?P?_ r -cell $_SDFF_?P?_ r [-cell $_DFFE_??_ 01 -cell $_DFFE_?P??_ r -cell $_SDFFE_?P??_ r] [-cell $_ALDFF_?P_ x -cell $_ALDFFE_?P?_ x] [-cell $_DLATCH_?_ x]    ($_ALDFF_*_ only if -asyncprld, $_DLATCH_* only if not -asyncprld, $_*DFFE_* only if not -nodffe)
                zinit -all w:* t:$_DFF_?_ t:$_DFFE_??_ t:$_SDFF*    (only if -abc9 and -dff)
                techmap -D NO_LUT -map +/ecp5/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                ecp5_gsr
                attrmvcp -copy -attr syn_useioff
                opt_clean

            map_luts:
                abc          (only if -abc2)
                techmap -map +/ecp5/latches_map.v    (skip if -asyncprld)
                abc -dress -lut 4:7
                clean

            map_cells:
                techmap -map +/ecp5/cells_map.v    (skip if -vpr)
                opt_lut_ins -tech ecp5
                clean

            check:
                autoname
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            blif:
                opt_clean -purge                                     (vpr mode)
                write_blif -attr -cname -conn -param <file-name>     (vpr mode)
                write_blif -gates -attr -param <file-name>           (non-vpr mode)

            edif:
                write_edif <file-name>

            json:
                write_json <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_ecp5 [options]
        
        This command runs synthesis for ECP5 FPGAs.
        
            -top <module>
                use the specified module as top module
        
            -blif <file>
                write the design to the specified BLIF file. writing of an output file
                is omitted if this parameter is not specified.
        
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
        
            -vpr
                generate an output netlist (and BLIF file) suitable for VPR
                (this feature is experimental and incomplete)
        
            -nodsp
                do not map multipliers to MULT18X18D
        
            -no-rw-check
                marks all recognized read ports as "return don't-care value on
                read/write collision" (same result as setting the no_rw_check
                attribute on all memories).
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -specify +/ecp5/cells_sim.v +/ecp5/cells_bb.v
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
                techmap -map +/mul2dsp.v -map +/ecp5/dsp_map.v -D DSP_A_MAXWIDTH=18 -D DSP_B_MAXWIDTH=18  -D DSP_A_MINWIDTH=2 -D DSP_B_MINWIDTH=2  -D DSP_NAME=$__MUL18X18    (unless -nodsp)
                chtype -set $mul t:$__soft_mul    (unless -nodsp)
                alumacc
                opt
                memory -nomap [-no-rw-check]
                opt_clean
        
            map_ram:
                memory_libmap -lib +/ecp5/lutrams.txt -lib +/ecp5/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/ecp5/lutrams_map.v -map +/ecp5/brams_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                techmap -map +/techmap.v -map +/ecp5/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
        
            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 01 -cell $_DFF_?P?_ r -cell $_SDFF_?P?_ r [-cell $_DFFE_??_ 01 -cell $_DFFE_?P??_ r -cell $_SDFFE_?P??_ r] [-cell $_ALDFF_?P_ x -cell $_ALDFFE_?P?_ x] [-cell $_DLATCH_?_ x]    ($_ALDFF_*_ only if -asyncprld, $_DLATCH_* only if not -asyncprld, $_*DFFE_* only if not -nodffe)
                zinit -all w:* t:$_DFF_?_ t:$_DFFE_??_ t:$_SDFF*    (only if -abc9 and -dff)
                techmap -D NO_LUT -map +/ecp5/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                ecp5_gsr
                attrmvcp -copy -attr syn_useioff
                opt_clean
        
            map_luts:
                abc          (only if -abc2)
                techmap -map +/ecp5/latches_map.v    (skip if -asyncprld)
                abc -dress -lut 4:7
                clean
        
            map_cells:
                techmap -map +/ecp5/cells_map.v    (skip if -vpr)
                opt_lut_ins -tech ecp5
                clean
        
            check:
                autoname
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            blif:
                opt_clean -purge                                     (vpr mode)
                write_blif -attr -cname -conn -param <file-name>     (vpr mode)
                write_blif -gates -attr -param <file-name>           (non-vpr mode)
        
            edif:
                write_edif <file-name>
        
            json:
                write_json <file-name>
        
