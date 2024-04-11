============================================================
synth_coolrunner2 - synthesis for Xilinx Coolrunner-II CPLDs
============================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synth_coolrunner2
    :title: synthesis for Xilinx Coolrunner-II CPLDs



    .. code:: yoscrypt

        synth_coolrunner2 [options]

    ::

        This command runs synthesis for Coolrunner-II CPLDs. This work is experimental.
        It is intended to be used with https://github.com/azonenberg/openfpga as the
        place-and-route.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified module as top module (default='top')


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



    ::

        The following commands are executed by this synthesis command:

            begin:
                read_verilog -lib +/coolrunner2/cells_sim.v
                hierarchy -check -top <top>

            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic

            coarse:
                synth -run coarse

            fine:
                extract_counter -dir up -allow_arst no
                techmap -map +/coolrunner2/cells_counter_map.v
                clean
                opt -fast -full
                techmap -map +/techmap.v -map +/coolrunner2/cells_latch.v
                opt -fast
                dfflibmap -prepare -liberty +/coolrunner2/xc2_dff.lib

            map_tff:
                abc -g AND,XOR
                clean
                extract -map +/coolrunner2/tff_extract.v

            map_pla:
                abc -sop -I 40 -P 56
                clean

            map_cells:
                dfflibmap -liberty +/coolrunner2/xc2_dff.lib
                dffinit -ff FDCP Q INIT
                dffinit -ff FDCP_N Q INIT
                dffinit -ff FTCP Q INIT
                dffinit -ff FTCP_N Q INIT
                dffinit -ff LDCP Q INIT
                dffinit -ff LDCP_N Q INIT
                coolrunner2_sop
                clean
                iopadmap -bits -inpad IBUF O:I -outpad IOBUFE I:IO -inoutpad IOBUFE O:IO -toutpad IOBUFE E:I:IO -tinoutpad IOBUFE E:O:I:IO
                attrmvcp -attr src -attr LOC t:IOBUFE n:*
                attrmvcp -attr src -attr LOC -driven t:IBUF n:*
                coolrunner2_fixup
                splitnets
                clean

            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox

            json:
                write_json <file-name>

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synth_coolrunner2 [options]
        
        This command runs synthesis for Coolrunner-II CPLDs. This work is experimental.
        It is intended to be used with https://github.com/azonenberg/openfpga as the
        place-and-route.
        
            -top <module>
                use the specified module as top module (default='top')
        
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
        
        
        The following commands are executed by this synthesis command:
        
            begin:
                read_verilog -lib +/coolrunner2/cells_sim.v
                hierarchy -check -top <top>
        
            flatten:    (unless -noflatten)
                proc
                flatten
                tribuf -logic
        
            coarse:
                synth -run coarse
        
            fine:
                extract_counter -dir up -allow_arst no
                techmap -map +/coolrunner2/cells_counter_map.v
                clean
                opt -fast -full
                techmap -map +/techmap.v -map +/coolrunner2/cells_latch.v
                opt -fast
                dfflibmap -prepare -liberty +/coolrunner2/xc2_dff.lib
        
            map_tff:
                abc -g AND,XOR
                clean
                extract -map +/coolrunner2/tff_extract.v
        
            map_pla:
                abc -sop -I 40 -P 56
                clean
        
            map_cells:
                dfflibmap -liberty +/coolrunner2/xc2_dff.lib
                dffinit -ff FDCP Q INIT
                dffinit -ff FDCP_N Q INIT
                dffinit -ff FTCP Q INIT
                dffinit -ff FTCP_N Q INIT
                dffinit -ff LDCP Q INIT
                dffinit -ff LDCP_N Q INIT
                coolrunner2_sop
                clean
                iopadmap -bits -inpad IBUF O:I -outpad IOBUFE I:IO -inoutpad IOBUFE O:IO -toutpad IOBUFE E:I:IO -tinoutpad IOBUFE E:O:I:IO
                attrmvcp -attr src -attr LOC t:IOBUFE n:*
                attrmvcp -attr src -attr LOC -driven t:IBUF n:*
                coolrunner2_fixup
                splitnets
                clean
        
            check:
                hierarchy -check
                stat
                check -noinit
                blackbox =A:whitebox
        
            json:
                write_json <file-name>
        
