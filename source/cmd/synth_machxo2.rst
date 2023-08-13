=======================================================================
synth_machxo2 - synthesis for MachXO2 FPGAs. This work is experimental.
=======================================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_machxo2
    :title: synthesis for MachXO2 FPGAs. This work is experimental.



    .. code:: yoscrypt

        synth_machxo2 [options]

    ::

        This command runs synthesis for MachXO2 FPGAs.


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

        -nobram

    ::

            do not use block RAM cells in output netlist


    .. code:: yoscrypt

        -nolutram

    ::

            do not use LUT RAM cells in output netlist


    .. code:: yoscrypt

        -noflatten

    ::

            do not flatten design before synthesis


    .. code:: yoscrypt

        -noiopad

    ::

            do not insert IO buffers


    .. code:: yoscrypt

        -ccu2

    ::

            use CCU2 cells in output netlist


    .. code:: yoscrypt

        -vpr

    ::

            generate an output netlist (and BLIF file) suitable for VPR
            (this feature is experimental and incomplete)



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib -icells +/machxo2/cells_sim.v +/machxo2/cells_bb.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout

            coarse:
                synth -run coarse

            map_ram:
                memory_libmap -lib +/machxo2/lutrams.txt -lib +/machxo2/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/machxo2/lutrams_map.v -map +/machxo2/brams_map.v

            fine:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:    (unless -noiopad)
                techmap
                iopadmap -bits -outpad OB I:O -inpad IB O:I -toutpad OBZ ~T:I:O -tinoutpad BB ~T:O:I:B A:top    (only if '-iopad')
                attrmvcp -attr src -attr LOC t:OB %x:+[O] t:OBZ %x:+[O] t:BB %x:+[B]
                attrmvcp -attr src -attr LOC -driven t:IB %x:+[I]

            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 01 -cell $_DFF_?P?_ r -cell $_SDFF_?P?_ r
                techmap -D NO_LUT -map +/machxo2/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                ecp5_gsr
                attrmvcp -copy -attr syn_useioff
                opt_clean

            map_luts:
                abc -lut 4 -dress
                clean

            map_cells:
                techmap -map +/machxo2/cells_map.v
                clean

            check:
                hierarchy -check
                stat
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

        
            synth_machxo2 [options]
        
        This command runs synthesis for MachXO2 FPGAs.
        
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
        
            -nobram
                do not use block RAM cells in output netlist
        
            -nolutram
                do not use LUT RAM cells in output netlist
        
            -noflatten
                do not flatten design before synthesis
        
            -noiopad
                do not insert IO buffers
        
            -ccu2
                use CCU2 cells in output netlist
        
            -vpr
                generate an output netlist (and BLIF file) suitable for VPR
                (this feature is experimental and incomplete)
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib -icells +/machxo2/cells_sim.v +/machxo2/cells_bb.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
                deminout
        
            coarse:
                synth -run coarse
        
            map_ram:
                memory_libmap -lib +/machxo2/lutrams.txt -lib +/machxo2/brams.txt [-no-auto-block] [-no-auto-distributed]    (-no-auto-block if -nobram, -no-auto-distributed if -nolutram)
                techmap -map +/machxo2/lutrams_map.v -map +/machxo2/brams_map.v
        
            fine:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:    (unless -noiopad)
                techmap
                iopadmap -bits -outpad OB I:O -inpad IB O:I -toutpad OBZ ~T:I:O -tinoutpad BB ~T:O:I:B A:top    (only if '-iopad')
                attrmvcp -attr src -attr LOC t:OB %x:+[O] t:OBZ %x:+[O] t:BB %x:+[B]
                attrmvcp -attr src -attr LOC -driven t:IB %x:+[I]
        
            map_ffs:
                opt_clean
                dfflegalize -cell $_DFF_?_ 01 -cell $_DFF_?P?_ r -cell $_SDFF_?P?_ r
                techmap -D NO_LUT -map +/machxo2/cells_map.v
                opt_expr -undriven -mux_undef
                simplemap
                ecp5_gsr
                attrmvcp -copy -attr syn_useioff
                opt_clean
        
            map_luts:
                abc -lut 4 -dress
                clean
        
            map_cells:
                techmap -map +/machxo2/cells_map.v
                clean
        
            check:
                hierarchy -check
                stat
                blackbox =A:whitebox
        
            blif:
                opt_clean -purge                                     (vpr mode)
                write_blif -attr -cname -conn -param <file-name>     (vpr mode)
                write_blif -gates -attr -param <file-name>           (non-vpr mode)
        
            edif:
                write_edif <file-name>
        
            json:
                write_json <file-name>
        
