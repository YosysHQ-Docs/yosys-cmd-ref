=======================================
synth_ice40 - synthesis for iCE40 FPGAs
=======================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help synth_ice40`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        synth_ice40 [options]

    ::

        This command runs synthesis for iCE40 FPGAs.


    .. code:: yoscrypt

        -device < hx | lp | u >

    ::

            relevant only for '-abc9' flow, optimise timing for the specified
            device. default: hx


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

        -nocarry

    ::

            do not use SB_CARRY cells in output netlist


    .. code:: yoscrypt

        -nodffe

    ::

            do not use SB_DFFE* cells in output netlist


    .. code:: yoscrypt

        -dffe_min_ce_use <min_ce_use>

    ::

            do not use SB_DFFE* cells if the resulting CE line would go to less
            than min_ce_use SB_DFFE* in output netlist


    .. code:: yoscrypt

        -nobram

    ::

            do not use SB_RAM40_4K* cells in output netlist


    .. code:: yoscrypt

        -spram

    ::

            enable automatic inference of SB_SPRAM256KA


    .. code:: yoscrypt

        -dsp

    ::

            use iCE40 UltraPlus DSP cells for large arithmetic


    .. code:: yoscrypt

        -noabc

    ::

            use built-in Yosys LUT techmapping instead of abc


    .. code:: yoscrypt

        -abc2

    ::

            run two passes of 'abc' for slightly improved logic density


    .. code:: yoscrypt

        -vpr

    ::

            generate an output netlist (and BLIF file) suitable for VPR
            (this feature is experimental and incomplete)


    .. code:: yoscrypt

        -abc9

    ::

            use new ABC9 flow (EXPERIMENTAL)


    .. code:: yoscrypt

        -flowmap

    ::

            use FlowMap LUT techmapping instead of abc (EXPERIMENTAL)


    .. code:: yoscrypt

        -no-rw-check

    ::

            marks all recognized read ports as "return don't-care value on
            read/write collision" (same result as setting the no_rw_check
            attribute on all memories).



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -D ICE40_HX -lib -specify +/ice40/cells_sim.v
                hierarchy -check -top <top>
                proc

            flatten:    (unless -noflatten)
                flatten
                tribuf -logic
                deminout

            coarse:
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
                memory_dff [-no-rw-check]
                wreduce t:$mul
                techmap -map +/mul2dsp.v -map +/ice40/dsp_map.v -D DSP_A_MAXWIDTH=16 -D DSP_B_MAXWIDTH=16 -D DSP_A_MINWIDTH=2 -D DSP_B_MINWIDTH=2 -D DSP_Y_MINWIDTH=11 -D DSP_NAME=$__MUL16X16    (if -dsp)
                select a:mul2dsp                  (if -dsp)
                setattr -unset mul2dsp            (if -dsp)
                opt_expr -fine                    (if -dsp)
                wreduce                           (if -dsp)
                select -clear                     (if -dsp)
                ice40_dsp                         (if -dsp)
                chtype -set $mul t:$__soft_mul    (if -dsp)
                alumacc
                opt
                memory -nomap [-no-rw-check]
                opt_clean

            map_ram:
                memory_libmap -lib +/ice40/brams.txt -lib +/ice40/spram.txt -no-auto-huge [-no-auto-huge] [-no-auto-block]    (-no-auto-huge unless -spram, -no-auto-block if -nobram)
                techmap -map +/ice40/brams_map.v -map +/ice40/spram_map.v
                ice40_braminit

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                ice40_wrapcarry
                techmap -map +/techmap.v -map +/ice40/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
                ice40_opt

            map_ffs:
                dfflegalize -cell $_DFF_?_ 0 -cell $_DFFE_?P_ 0 -cell $_DFF_?P?_ 0 -cell $_DFFE_?P?P_ 0 -cell $_SDFF_?P?_ 0 -cell $_SDFFCE_?P?P_ 0 -cell $_DLATCH_?_ x -mince -1
                techmap -map +/ice40/ff_map.v
                opt_expr -mux_undef
                simplemap
                ice40_opt -full

            map_luts:
                abc          (only if -abc2)
                ice40_opt    (only if -abc2)
                techmap -map +/ice40/latches_map.v
                simplemap                                   (if -noabc or -flowmap)
                techmap -map +/gate2lut.v -D LUT_WIDTH=4    (only if -noabc)
                flowmap -maxlut 4    (only if -flowmap)
                abc -dress -lut 4     (skip if -noabc)
                ice40_wrapcarry -unwrap
                techmap -map +/ice40/ff_map.v
                clean
                opt_lut -dlogic SB_CARRY:I0=1:I1=2:CI=3 -dlogic SB_CARRY:CO=3

            map_cells:
                techmap -map +/ice40/cells_map.v    (skip if -vpr)
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

        
            synth_ice40 [options]
        
        This command runs synthesis for iCE40 FPGAs.
        
            -device < hx | lp | u >
                relevant only for '-abc9' flow, optimise timing for the specified
                device. default: hx
        
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
        
            -nocarry
                do not use SB_CARRY cells in output netlist
        
            -nodffe
                do not use SB_DFFE* cells in output netlist
        
            -dffe_min_ce_use <min_ce_use>
                do not use SB_DFFE* cells if the resulting CE line would go to less
                than min_ce_use SB_DFFE* in output netlist
        
            -nobram
                do not use SB_RAM40_4K* cells in output netlist
        
            -spram
                enable automatic inference of SB_SPRAM256KA
        
            -dsp
                use iCE40 UltraPlus DSP cells for large arithmetic
        
            -noabc
                use built-in Yosys LUT techmapping instead of abc
        
            -abc2
                run two passes of 'abc' for slightly improved logic density
        
            -vpr
                generate an output netlist (and BLIF file) suitable for VPR
                (this feature is experimental and incomplete)
        
            -abc9
                use new ABC9 flow (EXPERIMENTAL)
        
            -flowmap
                use FlowMap LUT techmapping instead of abc (EXPERIMENTAL)
        
            -no-rw-check
                marks all recognized read ports as "return don't-care value on
                read/write collision" (same result as setting the no_rw_check
                attribute on all memories).
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -D ICE40_HX -lib -specify +/ice40/cells_sim.v
                hierarchy -check -top <top>
                proc
        
            flatten:    (unless -noflatten)
                flatten
                tribuf -logic
                deminout
        
            coarse:
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
                memory_dff [-no-rw-check]
                wreduce t:$mul
                techmap -map +/mul2dsp.v -map +/ice40/dsp_map.v -D DSP_A_MAXWIDTH=16 -D DSP_B_MAXWIDTH=16 -D DSP_A_MINWIDTH=2 -D DSP_B_MINWIDTH=2 -D DSP_Y_MINWIDTH=11 -D DSP_NAME=$__MUL16X16    (if -dsp)
                select a:mul2dsp                  (if -dsp)
                setattr -unset mul2dsp            (if -dsp)
                opt_expr -fine                    (if -dsp)
                wreduce                           (if -dsp)
                select -clear                     (if -dsp)
                ice40_dsp                         (if -dsp)
                chtype -set $mul t:$__soft_mul    (if -dsp)
                alumacc
                opt
                memory -nomap [-no-rw-check]
                opt_clean
        
            map_ram:
                memory_libmap -lib +/ice40/brams.txt -lib +/ice40/spram.txt -no-auto-huge [-no-auto-huge] [-no-auto-block]    (-no-auto-huge unless -spram, -no-auto-block if -nobram)
                techmap -map +/ice40/brams_map.v -map +/ice40/spram_map.v
                ice40_braminit
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                ice40_wrapcarry
                techmap -map +/techmap.v -map +/ice40/arith_map.v
                opt -fast
                abc -dff -D 1    (only if -retime)
                ice40_opt
        
            map_ffs:
                dfflegalize -cell $_DFF_?_ 0 -cell $_DFFE_?P_ 0 -cell $_DFF_?P?_ 0 -cell $_DFFE_?P?P_ 0 -cell $_SDFF_?P?_ 0 -cell $_SDFFCE_?P?P_ 0 -cell $_DLATCH_?_ x -mince -1
                techmap -map +/ice40/ff_map.v
                opt_expr -mux_undef
                simplemap
                ice40_opt -full
        
            map_luts:
                abc          (only if -abc2)
                ice40_opt    (only if -abc2)
                techmap -map +/ice40/latches_map.v
                simplemap                                   (if -noabc or -flowmap)
                techmap -map +/gate2lut.v -D LUT_WIDTH=4    (only if -noabc)
                flowmap -maxlut 4    (only if -flowmap)
                abc -dress -lut 4     (skip if -noabc)
                ice40_wrapcarry -unwrap
                techmap -map +/ice40/ff_map.v
                clean
                opt_lut -dlogic SB_CARRY:I0=1:I1=2:CI=3 -dlogic SB_CARRY:CO=3
        
            map_cells:
                techmap -map +/ice40/cells_map.v    (skip if -vpr)
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
        
