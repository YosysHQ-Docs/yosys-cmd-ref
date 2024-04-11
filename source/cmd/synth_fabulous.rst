==========================================
synth_fabulous - FABulous synthesis script
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_fabulous
    :title: FABulous synthesis script



    .. code:: yoscrypt

        synth_fabulous [options]

    ::

        This command runs synthesis for FPGA fabrics generated with FABulous. This command does not operate
        on partly selected designs.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module (default='top')


    .. code:: yoscrypt

        -auto-top

    ::

            automatically determine the top of the design hierarchy


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

        -lut <k>

    ::

            perform synthesis for a k-LUT architecture (default 4).


    .. code:: yoscrypt

        -vpr

    ::

            perform synthesis for the FABulous VPR flow (using slightly different techmapping).


    .. code:: yoscrypt

        -plib <primitive_library.v>

    ::

            use the specified Verilog file as a primitive library.


    .. code:: yoscrypt

        -extra-plib <primitive_library.v>

    ::

            use the specified Verilog file for extra primitives (can be specified multiple
            times).


    .. code:: yoscrypt

        -extra-map <techamp.v>

    ::

            use the specified Verilog file for extra techmap rules (can be specified multiple
            times).


    .. code:: yoscrypt

        -encfile <file>

    ::

            passed to 'fsm_recode' via 'fsm'


    .. code:: yoscrypt

        -nofsm

    ::

            do not run FSM optimization


    .. code:: yoscrypt

        -noalumacc

    ::

            do not run 'alumacc' pass. i.e. keep arithmetic operators in
            their direct form ($add, $sub, etc.).


    .. code:: yoscrypt

        -carry <none|ha>

    ::

            carry mapping style (none, half-adders, ...) default=none


    .. code:: yoscrypt

        -noregfile

    ::

            do not map register files


    .. code:: yoscrypt

        -iopad

    ::

            enable automatic insertion of IO buffers (otherwise a wrapper
            with manually inserted and constrained IO should be used.)


    .. code:: yoscrypt

        -complex-dff

    ::

            enable support for FFs with enable and synchronous SR (must also be
            supported by the target fabric.)


    .. code:: yoscrypt

        -noflatten

    ::

            do not flatten design after elaboration


    .. code:: yoscrypt

        -nordff

    ::

            passed to 'memory'. prohibits merging of FFs into memory read ports


    .. code:: yoscrypt

        -noshare

    ::

            do not run SAT-based resource sharing


    .. code:: yoscrypt

        -run <from_label>[:<to_label>]

    ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    .. code:: yoscrypt

        -no-rw-check

    ::

            marks all recognized read ports as "return don't-care value on
            read/write collision" (same result as setting the no_rw_check
            attribute on all memories).



    ::

        The following commands are executed by this synthesis command:
                read_verilog  -lib +/fabulous/prims.v
                read_verilog -lib <extra_plib.v>    (for each -extra-plib)

            begin:
                hierarchy -check
                proc

            flatten:    (unless -noflatten)
                flatten
                tribuf -logic
                deminout

            coarse:
                tribuf -logic
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm          (unless -nofsm)
                opt
                wreduce
                peepopt
                opt_clean
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v     (if -lut)
                alumacc      (unless -noalumacc)
                share        (unless -noshare)
                opt
                memory -nomap
                opt_clean

            map_ram:
                memory_libmap -lib +/fabulous/ram_regfile.txt
                techmap -map +/fabulous/regfile_map.v

            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine

            map_gates:
                opt -full
                techmap -map +/techmap.v -map +/fabulous/arith_map.v -D ARITH_<carry>
                opt -fast

            map_iopad:    (if -iopad)

            map_ffs:
                dfflegalize -cell $_DFF_P_ 0 -cell $_DLATCH_?_ x    without -complex-dff
                techmap -map +/fabulous/latches_map.v
                techmap -map +/fabulous/ff_map.v
                techmap -map <extra_map.v>...    (for each -extra-map)
                clean

            map_luts:
                abc -lut 4 -dress
                clean

            map_cells:
                techmap -D LUT_K=4 -map +/fabulous/cells_map.v
                clean

            check:
                hierarchy -check
                stat

            blif:
                opt_clean -purge
                write_blif -attr -cname -conn -param <file-name>

            json:
                write_json <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_fabulous [options]
        
        This command runs synthesis for FPGA fabrics generated with FABulous. This command does not operate
        on partly selected designs.
        
            -top <module>
                use the specified module as top module (default='top')
        
            -auto-top
                automatically determine the top of the design hierarchy
        
            -blif <file>
                write the design to the specified BLIF file. writing of an output file
                is omitted if this parameter is not specified.
        
            -edif <file>
                write the design to the specified EDIF file. writing of an output file
                is omitted if this parameter is not specified.
        
            -json <file>
                write the design to the specified JSON file. writing of an output file
                is omitted if this parameter is not specified.
        
            -lut <k>
                perform synthesis for a k-LUT architecture (default 4).
        
            -vpr
                perform synthesis for the FABulous VPR flow (using slightly different techmapping).
        
            -plib <primitive_library.v>
                use the specified Verilog file as a primitive library.
        
            -extra-plib <primitive_library.v>
                use the specified Verilog file for extra primitives (can be specified multiple
                times).
        
            -extra-map <techamp.v>
                use the specified Verilog file for extra techmap rules (can be specified multiple
                times).
        
            -encfile <file>
                passed to 'fsm_recode' via 'fsm'
        
            -nofsm
                do not run FSM optimization
        
            -noalumacc
                do not run 'alumacc' pass. i.e. keep arithmetic operators in
                their direct form ($add, $sub, etc.).
        
            -carry <none|ha>
                carry mapping style (none, half-adders, ...) default=none
        
            -noregfile
                do not map register files
        
            -iopad
                enable automatic insertion of IO buffers (otherwise a wrapper
                with manually inserted and constrained IO should be used.)
        
            -complex-dff
                enable support for FFs with enable and synchronous SR (must also be
                supported by the target fabric.)
        
            -noflatten
                do not flatten design after elaboration
        
            -nordff
                passed to 'memory'. prohibits merging of FFs into memory read ports
        
            -noshare
                do not run SAT-based resource sharing
        
            -run <from_label>[:<to_label>]
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
            -no-rw-check
                marks all recognized read ports as "return don't-care value on
                read/write collision" (same result as setting the no_rw_check
                attribute on all memories).
        
        
        The following commands are executed by this synthesis command:
                read_verilog  -lib +/fabulous/prims.v
                read_verilog -lib <extra_plib.v>    (for each -extra-plib)
        
            begin:
                hierarchy -check
                proc
        
            flatten:    (unless -noflatten)
                flatten
                tribuf -logic
                deminout
        
            coarse:
                tribuf -logic
                deminout
                opt_expr
                opt_clean
                check
                opt -nodffe -nosdff
                fsm          (unless -nofsm)
                opt
                wreduce
                peepopt
                opt_clean
                techmap -map +/cmp2lut.v -map +/cmp2lcu.v     (if -lut)
                alumacc      (unless -noalumacc)
                share        (unless -noshare)
                opt
                memory -nomap
                opt_clean
        
            map_ram:
                memory_libmap -lib +/fabulous/ram_regfile.txt
                techmap -map +/fabulous/regfile_map.v
        
            map_ffram:
                opt -fast -mux_undef -undriven -fine
                memory_map
                opt -undriven -fine
        
            map_gates:
                opt -full
                techmap -map +/techmap.v -map +/fabulous/arith_map.v -D ARITH_<carry>
                opt -fast
        
            map_iopad:    (if -iopad)
        
            map_ffs:
                dfflegalize -cell $_DFF_P_ 0 -cell $_DLATCH_?_ x    without -complex-dff
                techmap -map +/fabulous/latches_map.v
                techmap -map +/fabulous/ff_map.v
                techmap -map <extra_map.v>...    (for each -extra-map)
                clean
        
            map_luts:
                abc -lut 4 -dress
                clean
        
            map_cells:
                techmap -D LUT_K=4 -map +/fabulous/cells_map.v
                clean
        
            check:
                hierarchy -check
                stat
        
            blif:
                opt_clean -purge
                write_blif -attr -cname -conn -param <file-name>
        
            json:
                write_json <file-name>
        
