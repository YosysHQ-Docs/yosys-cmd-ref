=================================================
synth_intel - synthesis for Intel (Altera) FPGAs.
=================================================

.. only:: html

    :code:`yosys> help synth_intel`
    ----------------------------------------------------------------------------


    :code:`synth_intel [options]` ::

        This command runs synthesis for Intel FPGAs.


    :code:`-family <max10 | cyclone10lp | cycloneiv | cycloneive>` ::

            generate the synthesis netlist for the specified family.
            MAX10 is the default target if no family argument specified.
            For Cyclone IV GX devices, use cycloneiv argument; for Cyclone IV E, use
            cycloneive. For Cyclone V and Cyclone 10 GX, use the synth_intel_alm
            backend instead.


    :code:`-top <module>` ::

            use the specified module as top module (default='top')


    :code:`-vqm <file>` ::

            write the design to the specified Verilog Quartus Mapping File. Writing
            of an output file is omitted if this parameter is not specified.
            Note that this backend has not been tested and is likely incompatible
            with recent versions of Quartus.


    :code:`-vpr <file>` ::

            write BLIF files for VPR flow experiments. The synthesized BLIF output
            file is not compatible with the Quartus flow. Writing of an
            output file is omitted if this parameter is not specified.


    :code:`-run <from_label>:<to_label>` ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    :code:`-iopads` ::

            use IO pad cells in output netlist


    :code:`-nobram` ::

            do not use block RAM cells in output netlist


    :code:`-noflatten` ::

            do not flatten design before synthesis


    :code:`-retime` ::

            run 'abc' with '-dff -D 1' options


    ::

        The following commands are executed by this synthesis command:

            begin:

            family:
                read_verilog -sv -lib +/intel/max10/cells_sim.v
                read_verilog -sv -lib +/intel/common/m9k_bb.v
                read_verilog -sv -lib +/intel/common/altpll_bb.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout

            coarse:
                synth -run coarse

            map_bram:    (skip if -nobram)
                memory_bram -rules +/intel/common/brams_m9k.txt    (if applicable for family)
                techmap -map +/intel/common/brams_map_m9k.v    (if applicable for family)

            map_ffram:
                opt -fast -mux_undef -undriven -fine -full
                memory_map
                opt -undriven -fine
                techmap -map +/techmap.v
                opt -full
                clean -purge
                setundef -undriven -zero
                abc -markgroups -dff -D 1    (only if -retime)

            map_ffs:
                dfflegalize -cell $_DFFE_PN0P_ 01
                techmap -map +/intel/common/ff_map.v

            map_luts:
                abc -lut 4
                clean

            map_cells:
                iopadmap -bits -outpad $__outpad I:O -inpad $__inpad O:I    (if -iopads)
                techmap -map +/intel/max10/cells_map.v
                clean -purge

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            vqm:
                write_verilog -attr2comment -defparam -nohex -decimal -renameprefix syn_ <file-name>

            vpr:
                opt_clean -purge
                write_blif <file-name>


        WARNING: THE 'synth_intel' COMMAND IS EXPERIMENTAL.

.. only:: latex

    ::

        
            synth_intel [options]
        
        This command runs synthesis for Intel FPGAs.
        
            -family <max10 | cyclone10lp | cycloneiv | cycloneive>
                generate the synthesis netlist for the specified family.
                MAX10 is the default target if no family argument specified.
                For Cyclone IV GX devices, use cycloneiv argument; for Cyclone IV E, use
                cycloneive. For Cyclone V and Cyclone 10 GX, use the synth_intel_alm
                backend instead.
        
            -top <module>
                use the specified module as top module (default='top')
        
            -vqm <file>
                write the design to the specified Verilog Quartus Mapping File. Writing
                of an output file is omitted if this parameter is not specified.
                Note that this backend has not been tested and is likely incompatible
                with recent versions of Quartus.
        
            -vpr <file>
                write BLIF files for VPR flow experiments. The synthesized BLIF output
                file is not compatible with the Quartus flow. Writing of an
                output file is omitted if this parameter is not specified.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -iopads
                use IO pad cells in output netlist
        
            -nobram
                do not use block RAM cells in output netlist
        
            -noflatten
                do not flatten design before synthesis
        
            -retime
                run 'abc' with '-dff -D 1' options
        
        The following commands are executed by this synthesis command:
        
            begin:
        
            family:
                read_verilog -sv -lib +/intel/max10/cells_sim.v
                read_verilog -sv -lib +/intel/common/m9k_bb.v
                read_verilog -sv -lib +/intel/common/altpll_bb.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout
        
            coarse:
                synth -run coarse
        
            map_bram:    (skip if -nobram)
                memory_bram -rules +/intel/common/brams_m9k.txt    (if applicable for family)
                techmap -map +/intel/common/brams_map_m9k.v    (if applicable for family)
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine -full
                memory_map
                opt -undriven -fine
                techmap -map +/techmap.v
                opt -full
                clean -purge
                setundef -undriven -zero
                abc -markgroups -dff -D 1    (only if -retime)
        
            map_ffs:
                dfflegalize -cell $_DFFE_PN0P_ 01
                techmap -map +/intel/common/ff_map.v
        
            map_luts:
                abc -lut 4
                clean
        
            map_cells:
                iopadmap -bits -outpad $__outpad I:O -inpad $__inpad O:I    (if -iopads)
                techmap -map +/intel/max10/cells_map.v
                clean -purge
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            vqm:
                write_verilog -attr2comment -defparam -nohex -decimal -renameprefix syn_ <file-name>
        
            vpr:
                opt_clean -purge
                write_blif <file-name>
        
        
        WARNING: THE 'synth_intel' COMMAND IS EXPERIMENTAL.
        
