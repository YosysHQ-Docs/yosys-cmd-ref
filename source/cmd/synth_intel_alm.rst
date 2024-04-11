===============================================================
synth_intel_alm - synthesis for ALM-based Intel (Altera) FPGAs.
===============================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_intel_alm
    :title: synthesis for ALM-based Intel (Altera) FPGAs.



    .. code:: yoscrypt

        synth_intel_alm [options]

    ::

        This command runs synthesis for ALM-based Intel FPGAs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module


    .. code:: yoscrypt

        -family <family>

    ::

            target one of:
            "cyclonev"    - Cyclone V (default)
            "arriav"      - Arria V (non-GZ)
            "cyclone10gx" - Cyclone 10GX


    .. code:: yoscrypt

        -vqm <file>

    ::

            write the design to the specified Verilog Quartus Mapping File. Writing
            of an output file is omitted if this parameter is not specified. Implies
            -quartus.


    .. code:: yoscrypt

        -noflatten

    ::

            do not flatten design before synthesis; useful for per-module area
            statistics


    .. code:: yoscrypt

        -quartus

    ::

            output a netlist using Quartus cells instead of MISTRAL_* cells


    .. code:: yoscrypt

        -dff

    ::

            pass DFFs to ABC to perform sequential logic optimisations
            (EXPERIMENTAL)


    .. code:: yoscrypt

        -run <from_label>:<to_label>

    ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -nolutram

    ::

            do not use LUT RAM cells in output netlist


    .. code:: yoscrypt

        -nobram

    ::

            do not use block RAM cells in output netlist


    .. code:: yoscrypt

        -nodsp

    ::

            do not map multipliers to MISTRAL_MUL cells


    .. code:: yoscrypt

        -noiopad

    ::

            do not instantiate IO buffers


    .. code:: yoscrypt

        -noclkbuf

    ::

            do not insert global clock buffers


    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -specify -lib -D <family> +/intel_alm/common/alm_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/dff_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/dsp_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/mem_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/misc_sim.v
                read_verilog -specify -lib -D <family> -icells +/intel_alm/common/abc9_model.v
                read_verilog -lib +/intel/common/altpll_bb.v
                read_verilog -lib +/intel_alm/common/megafunction_bb.v
                hierarchy -check -top <top>

            coarse:
                proc
                flatten    (skip if -noflatten)
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
                techmap -map +/cmp2lut.v -D LUT_WIDTH=6
                opt_expr
                opt_clean
                techmap -map +/mul2dsp.v [...]    (unless -nodsp)
                alumacc
                iopadmap -bits -outpad MISTRAL_OB I:PAD -inpad MISTRAL_IB O:PAD -toutpad MISTRAL_IO OE:O:PAD -tinoutpad MISTRAL_IO OE:O:I:PAD A:top    (unless -noiopad)
                techmap -map +/intel_alm/common/arith_alm_map.v -map +/intel_alm/common/dsp_map.v
                opt
                memory -nomap
                opt_clean

            map_bram:    (skip if -nobram)
                memory_bram -rules +/intel_alm/common/bram_<bram_type>.txt
                techmap -map +/intel_alm/common/bram_<bram_type>_map.v

            map_lutram:    (skip if -nolutram)
                memory_bram -rules +/intel_alm/common/lutram_mlab.txt    (for Cyclone V / Cyclone 10GX)

            map_ffram:
                memory_map
                opt -full

            map_ffs:
                techmap
                dfflegalize -cell $_DFFE_PN0P_ 0 -cell $_SDFFCE_PP0P_ 0
                techmap -map +/intel_alm/common/dff_map.v
                opt -full -undriven -mux_undef
                clean -purge
                clkbufmap -buf MISTRAL_CLKBUF Q:A    (unless -noclkbuf)

            map_luts:
                techmap -map +/intel_alm/common/abc9_map.v
                abc9 [-dff] -maxlut 6 -W 600
                techmap -map +/intel_alm/common/abc9_unmap.v
                techmap -map +/intel_alm/common/alm_map.v
                opt -fast
                autoname
                clean

            check:
                hierarchy -check
                stat
                check
                blackbox =A:whitebox

            quartus:
                rename -hide w:*[* w:*]*
                setundef -zero
                hilomap -singleton -hicell __MISTRAL_VCC Q -locell __MISTRAL_GND Q
                techmap -D <family> -map +/intel_alm/common/quartus_rename.v

            vqm:
                write_verilog -attr2comment -defparam -nohex -decimal <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_intel_alm [options]
        
        This command runs synthesis for ALM-based Intel FPGAs.
        
            -top <module>
                use the specified module as top module
        
            -family <family>
                target one of:
                "cyclonev"    - Cyclone V (default)
                "arriav"      - Arria V (non-GZ)
                "cyclone10gx" - Cyclone 10GX
        
            -vqm <file>
                write the design to the specified Verilog Quartus Mapping File. Writing
                of an output file is omitted if this parameter is not specified. Implies
                -quartus.
        
            -noflatten
                do not flatten design before synthesis; useful for per-module area
                statistics
        
            -quartus
                output a netlist using Quartus cells instead of MISTRAL_* cells
        
            -dff
                pass DFFs to ABC to perform sequential logic optimisations
                (EXPERIMENTAL)
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -nolutram
                do not use LUT RAM cells in output netlist
        
            -nobram
                do not use block RAM cells in output netlist
        
            -nodsp
                do not map multipliers to MISTRAL_MUL cells
        
            -noiopad
                do not instantiate IO buffers
        
            -noclkbuf
                do not insert global clock buffers
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -specify -lib -D <family> +/intel_alm/common/alm_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/dff_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/dsp_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/mem_sim.v
                read_verilog -specify -lib -D <family> +/intel_alm/common/misc_sim.v
                read_verilog -specify -lib -D <family> -icells +/intel_alm/common/abc9_model.v
                read_verilog -lib +/intel/common/altpll_bb.v
                read_verilog -lib +/intel_alm/common/megafunction_bb.v
                hierarchy -check -top <top>
        
            coarse:
                proc
                flatten    (skip if -noflatten)
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
                techmap -map +/cmp2lut.v -D LUT_WIDTH=6
                opt_expr
                opt_clean
                techmap -map +/mul2dsp.v [...]    (unless -nodsp)
                alumacc
                iopadmap -bits -outpad MISTRAL_OB I:PAD -inpad MISTRAL_IB O:PAD -toutpad MISTRAL_IO OE:O:PAD -tinoutpad MISTRAL_IO OE:O:I:PAD A:top    (unless -noiopad)
                techmap -map +/intel_alm/common/arith_alm_map.v -map +/intel_alm/common/dsp_map.v
                opt
                memory -nomap
                opt_clean
        
            map_bram:    (skip if -nobram)
                memory_bram -rules +/intel_alm/common/bram_<bram_type>.txt
                techmap -map +/intel_alm/common/bram_<bram_type>_map.v
        
            map_lutram:    (skip if -nolutram)
                memory_bram -rules +/intel_alm/common/lutram_mlab.txt    (for Cyclone V / Cyclone 10GX)
        
            map_ffram:
                memory_map
                opt -full
        
            map_ffs:
                techmap
                dfflegalize -cell $_DFFE_PN0P_ 0 -cell $_SDFFCE_PP0P_ 0
                techmap -map +/intel_alm/common/dff_map.v
                opt -full -undriven -mux_undef
                clean -purge
                clkbufmap -buf MISTRAL_CLKBUF Q:A    (unless -noclkbuf)
        
            map_luts:
                techmap -map +/intel_alm/common/abc9_map.v
                abc9 [-dff] -maxlut 6 -W 600
                techmap -map +/intel_alm/common/abc9_unmap.v
                techmap -map +/intel_alm/common/alm_map.v
                opt -fast
                autoname
                clean
        
            check:
                hierarchy -check
                stat
                check
                blackbox =A:whitebox
        
            quartus:
                rename -hide w:*[* w:*]*
                setundef -zero
                hilomap -singleton -hicell __MISTRAL_VCC Q -locell __MISTRAL_GND Q
                techmap -D <family> -map +/intel_alm/common/quartus_rename.v
        
            vqm:
                write_verilog -attr2comment -defparam -nohex -decimal <file-name>
        
