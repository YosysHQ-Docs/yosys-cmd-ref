====================================
abc - use ABC for technology mapping
====================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: abc
    :title: use ABC for technology mapping



    .. code:: yoscrypt

        abc [options] [selection]

    ::

        This pass uses the ABC tool [1] for technology mapping of yosys's internal gate
        library to a target architecture.


    .. code:: yoscrypt

        -exe <command>

    ::

            use the specified command instead of "<yosys-bindir>/yosys-abc" to execute ABC.
            This can e.g. be used to call a specific version of ABC or a wrapper.


    .. code:: yoscrypt

        -script <file>

    ::

            use the specified ABC script file instead of the default script.

            if <file> starts with a plus sign (+), then the rest of the filename
            string is interpreted as the command string to be passed to ABC. The
            leading plus sign is removed and all commas (,) in the string are
            replaced with blanks before the string is passed to ABC.

            if no -script parameter is given, the following scripts are used:

            for -liberty/-genlib without -constr:
              strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                   &get -n; &dch -f; &nf {D}; &put

            for -liberty/-genlib with -constr:
              strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                   &get -n; &dch -f; &nf {D}; &put; buffer; upsize {D};
                   dnsize {D}; stime -p

            for -lut/-luts (only one LUT size):
              strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                   dch -f; if; mfs2; lutpack {S}

            for -lut/-luts (different LUT sizes):
              strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                   dch -f; if; mfs2

            for -sop:
              strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                   dch -f; cover {I} {P}

            otherwise:
              strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                   &get -n; &dch -f; &nf {D}; &put


    .. code:: yoscrypt

        -fast

    ::

            use different default scripts that are slightly faster (at the cost
            of output quality):

            for -liberty/-genlib without -constr:
              strash; dretime; map {D}

            for -liberty/-genlib with -constr:
              strash; dretime; map {D}; buffer; upsize {D}; dnsize {D};
                   stime -p

            for -lut/-luts:
              strash; dretime; if

            for -sop:
              strash; dretime; cover {I} {P}

            otherwise:
              strash; dretime; map


    .. code:: yoscrypt

        -liberty <file>

    ::

            generate netlists for the specified cell library (using the liberty
            file format).


    .. code:: yoscrypt

        -dont_use <cell_name>

    ::

            generate netlists for the specified cell library (using the liberty
            file format).


    .. code:: yoscrypt

        -genlib <file>

    ::

            generate netlists for the specified cell library (using the SIS Genlib
            file format).


    .. code:: yoscrypt

        -constr <file>

    ::

            pass this file with timing constraints to ABC.
            use with -liberty/-genlib.

            a constr file contains two lines:
                set_driving_cell <cell_name>
                set_load <floating_point_number>

            the set_driving_cell statement defines which cell type is assumed to
            drive the primary inputs and the set_load statement sets the load in
            femtofarads for each primary output.


    .. code:: yoscrypt

        -D <picoseconds>

    ::

            set delay target. the string {D} in the default scripts above is
            replaced by this option when used, and an empty string otherwise.
            this also replaces 'dretime' with 'dretime; retime -o {D}' in the
            default scripts above.


    .. code:: yoscrypt

        -I <num>

    ::

            maximum number of SOP inputs.
            (replaces {I} in the default scripts above)


    .. code:: yoscrypt

        -P <num>

    ::

            maximum number of SOP products.
            (replaces {P} in the default scripts above)


    .. code:: yoscrypt

        -S <num>

    ::

            maximum number of LUT inputs shared.
            (replaces {S} in the default scripts above, default: -S 1)


    .. code:: yoscrypt

        -lut <width>

    ::

            generate netlist using luts of (max) the specified width.


    .. code:: yoscrypt

        -lut <w1>:<w2>

    ::

            generate netlist using luts of (max) the specified width <w2>. All
            luts with width <= <w1> have constant cost. for luts larger than <w1>
            the area cost doubles with each additional input bit. the delay cost
            is still constant for all lut widths.


    .. code:: yoscrypt

        -luts <cost1>,<cost2>,<cost3>,<sizeN>:<cost4-N>,..

    ::

            generate netlist using luts. Use the specified costs for luts with 1,
            2, 3, .. inputs.


    .. code:: yoscrypt

        -sop

    ::

            map to sum-of-product cells and inverters


    .. code:: yoscrypt

        -g type1,type2,...

    ::

            Map to the specified list of gate types. Supported gates types are:
               AND, NAND, OR, NOR, XOR, XNOR, ANDNOT, ORNOT, MUX,
               NMUX, AOI3, OAI3, AOI4, OAI4.
            (The NOT gate is always added to this list automatically.)

            The following aliases can be used to reference common sets of gate
            types:
              simple: AND OR XOR MUX
              cmos2:  NAND NOR
              cmos3:  NAND NOR AOI3 OAI3
              cmos4:  NAND NOR AOI3 OAI3 AOI4 OAI4
              cmos:   NAND NOR AOI3 OAI3 AOI4 OAI4 NMUX MUX XOR XNOR
              gates:  AND NAND OR NOR XOR XNOR ANDNOT ORNOT
              aig:    AND NAND OR NOR ANDNOT ORNOT

            The alias 'all' represent the full set of all gate types.

            Prefix a gate type with a '-' to remove it from the list. For example
            the arguments 'AND,OR,XOR' and 'simple,-MUX' are equivalent.

            The default is 'all,-NMUX,-AOI3,-OAI3,-AOI4,-OAI4'.


    .. code:: yoscrypt

        -dff

    ::

            also pass $_DFF_?_ and $_DFFE_??_ cells through ABC. modules with many
            clock domains are automatically partitioned in clock domains and each
            domain is passed through ABC independently.


    .. code:: yoscrypt

        -clk [!]<clock-signal-name>[,[!]<enable-signal-name>]

    ::

            use only the specified clock domain. this is like -dff, but only FF
            cells that belong to the specified clock domain are used.


    .. code:: yoscrypt

        -keepff

    ::

            set the "keep" attribute on flip-flop output wires. (and thus preserve
            them, for example for equivalence checking.)


    .. code:: yoscrypt

        -nocleanup

    ::

            when this option is used, the temporary files created by this pass
            are not removed. this is useful for debugging.


    .. code:: yoscrypt

        -showtmp

    ::

            print the temp dir name in log. usually this is suppressed so that the
            command output is identical across runs.


    .. code:: yoscrypt

        -markgroups

    ::

            set a 'abcgroup' attribute on all objects created by ABC. The value of
            this attribute is a unique integer for each ABC process started. This
            is useful for debugging the partitioning of clock domains.


    .. code:: yoscrypt

        -dress

    ::

            run the 'dress' command after all other ABC commands. This aims to
            preserve naming by an equivalence check between the original and
            post-ABC netlists (experimental).


    ::

        When no target cell library is specified the Yosys standard cell library is
        loaded into ABC before the ABC script is executed.

        Note that this is a logic optimization pass within Yosys that is calling ABC
        internally. This is not going to "run ABC on your design". It will instead run
        ABC on logic snippets extracted from your design. You will not get any useful
        output when passing an ABC script that writes a file. Instead write your full
        design as BLIF file with write_blif and then load that into ABC externally if
        you want to use ABC to convert your design into another format.

        [1] http://www.eecs.berkeley.edu/~alanmi/abc/

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            abc [options] [selection]
        
        This pass uses the ABC tool [1] for technology mapping of yosys's internal gate
        library to a target architecture.
        
            -exe <command>
                use the specified command instead of "<yosys-bindir>/yosys-abc" to execute ABC.
                This can e.g. be used to call a specific version of ABC or a wrapper.
        
            -script <file>
                use the specified ABC script file instead of the default script.
        
                if <file> starts with a plus sign (+), then the rest of the filename
                string is interpreted as the command string to be passed to ABC. The
                leading plus sign is removed and all commas (,) in the string are
                replaced with blanks before the string is passed to ABC.
        
                if no -script parameter is given, the following scripts are used:
        
                for -liberty/-genlib without -constr:
                  strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                       &get -n; &dch -f; &nf {D}; &put
        
                for -liberty/-genlib with -constr:
                  strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                       &get -n; &dch -f; &nf {D}; &put; buffer; upsize {D};
                       dnsize {D}; stime -p
        
                for -lut/-luts (only one LUT size):
                  strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                       dch -f; if; mfs2; lutpack {S}
        
                for -lut/-luts (different LUT sizes):
                  strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                       dch -f; if; mfs2
        
                for -sop:
                  strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                       dch -f; cover {I} {P}
        
                otherwise:
                  strash; &get -n; &fraig -x; &put; scorr; dc2; dretime; strash;
                       &get -n; &dch -f; &nf {D}; &put
        
            -fast
                use different default scripts that are slightly faster (at the cost
                of output quality):
        
                for -liberty/-genlib without -constr:
                  strash; dretime; map {D}
        
                for -liberty/-genlib with -constr:
                  strash; dretime; map {D}; buffer; upsize {D}; dnsize {D};
                       stime -p
        
                for -lut/-luts:
                  strash; dretime; if
        
                for -sop:
                  strash; dretime; cover {I} {P}
        
                otherwise:
                  strash; dretime; map
        
            -liberty <file>
                generate netlists for the specified cell library (using the liberty
                file format).
        
            -dont_use <cell_name>
                generate netlists for the specified cell library (using the liberty
                file format).
        
            -genlib <file>
                generate netlists for the specified cell library (using the SIS Genlib
                file format).
        
            -constr <file>
                pass this file with timing constraints to ABC.
                use with -liberty/-genlib.
        
                a constr file contains two lines:
                    set_driving_cell <cell_name>
                    set_load <floating_point_number>
        
                the set_driving_cell statement defines which cell type is assumed to
                drive the primary inputs and the set_load statement sets the load in
                femtofarads for each primary output.
        
            -D <picoseconds>
                set delay target. the string {D} in the default scripts above is
                replaced by this option when used, and an empty string otherwise.
                this also replaces 'dretime' with 'dretime; retime -o {D}' in the
                default scripts above.
        
            -I <num>
                maximum number of SOP inputs.
                (replaces {I} in the default scripts above)
        
            -P <num>
                maximum number of SOP products.
                (replaces {P} in the default scripts above)
        
            -S <num>
                maximum number of LUT inputs shared.
                (replaces {S} in the default scripts above, default: -S 1)
        
            -lut <width>
                generate netlist using luts of (max) the specified width.
        
            -lut <w1>:<w2>
                generate netlist using luts of (max) the specified width <w2>. All
                luts with width <= <w1> have constant cost. for luts larger than <w1>
                the area cost doubles with each additional input bit. the delay cost
                is still constant for all lut widths.
        
            -luts <cost1>,<cost2>,<cost3>,<sizeN>:<cost4-N>,..
                generate netlist using luts. Use the specified costs for luts with 1,
                2, 3, .. inputs.
        
            -sop
                map to sum-of-product cells and inverters
        
            -g type1,type2,...
                Map to the specified list of gate types. Supported gates types are:
                   AND, NAND, OR, NOR, XOR, XNOR, ANDNOT, ORNOT, MUX,
                   NMUX, AOI3, OAI3, AOI4, OAI4.
                (The NOT gate is always added to this list automatically.)
        
                The following aliases can be used to reference common sets of gate
                types:
                  simple: AND OR XOR MUX
                  cmos2:  NAND NOR
                  cmos3:  NAND NOR AOI3 OAI3
                  cmos4:  NAND NOR AOI3 OAI3 AOI4 OAI4
                  cmos:   NAND NOR AOI3 OAI3 AOI4 OAI4 NMUX MUX XOR XNOR
                  gates:  AND NAND OR NOR XOR XNOR ANDNOT ORNOT
                  aig:    AND NAND OR NOR ANDNOT ORNOT
        
                The alias 'all' represent the full set of all gate types.
        
                Prefix a gate type with a '-' to remove it from the list. For example
                the arguments 'AND,OR,XOR' and 'simple,-MUX' are equivalent.
        
                The default is 'all,-NMUX,-AOI3,-OAI3,-AOI4,-OAI4'.
        
            -dff
                also pass $_DFF_?_ and $_DFFE_??_ cells through ABC. modules with many
                clock domains are automatically partitioned in clock domains and each
                domain is passed through ABC independently.
        
            -clk [!]<clock-signal-name>[,[!]<enable-signal-name>]
                use only the specified clock domain. this is like -dff, but only FF
                cells that belong to the specified clock domain are used.
        
            -keepff
                set the "keep" attribute on flip-flop output wires. (and thus preserve
                them, for example for equivalence checking.)
        
            -nocleanup
                when this option is used, the temporary files created by this pass
                are not removed. this is useful for debugging.
        
            -showtmp
                print the temp dir name in log. usually this is suppressed so that the
                command output is identical across runs.
        
            -markgroups
                set a 'abcgroup' attribute on all objects created by ABC. The value of
                this attribute is a unique integer for each ABC process started. This
                is useful for debugging the partitioning of clock domains.
        
            -dress
                run the 'dress' command after all other ABC commands. This aims to
                preserve naming by an equivalence check between the original and
                post-ABC netlists (experimental).
        
        When no target cell library is specified the Yosys standard cell library is
        loaded into ABC before the ABC script is executed.
        
        Note that this is a logic optimization pass within Yosys that is calling ABC
        internally. This is not going to "run ABC on your design". It will instead run
        ABC on logic snippets extracted from your design. You will not get any useful
        output when passing an ABC script that writes a file. Instead write your full
        design as BLIF file with write_blif and then load that into ABC externally if
        you want to use ABC to convert your design into another format.
        
        [1] http://www.eecs.berkeley.edu/~alanmi/abc/
        
