======================================
abc9 - use ABC9 for technology mapping
======================================

.. only:: html

    :code:`yosys> help abc9`
    ----------------------------------------------------------------------------


    :code:`abc9 [options] [selection]` ::

        This script pass performs a sequence of commands to facilitate the use of the
        ABC tool [1] for technology mapping of the current design to a target FPGA
        architecture. Only fully-selected modules are supported.


    :code:`-run <from_label>:<to_label>` ::

            only run the commands between the labels (see below). an empty
            from label is synonymous to 'begin', and empty to label is
            synonymous to the end of the command list.


    :code:`-exe <command>` ::

            use the specified command instead of "<yosys-bindir>/yosys-abc" to execute ABC.
            This can e.g. be used to call a specific version of ABC or a wrapper.


    :code:`-script <file>` ::

            use the specified ABC script file instead of the default script.

            if <file> starts with a plus sign (+), then the rest of the filename
            string is interpreted as the command string to be passed to ABC. The
            leading plus sign is removed and all commas (,) in the string are
            replaced with blanks before the string is passed to ABC.

            if no -script parameter is given, the following scripts are used:
              &scorr; &sweep; &dc2; &dch -f; &ps; &if {C} {W} {D} {R} -v; &mfs


    :code:`-fast` ::

            use different default scripts that are slightly faster (at the cost
            of output quality):
              &if {C} {W} {D} {R} -v


    :code:`-D <picoseconds>` ::

            set delay target. the string {D} in the default scripts above is
            replaced by this option when used, and an empty string otherwise
            (indicating best possible delay).


    :code:`-lut <width>` ::

            generate netlist using luts of (max) the specified width.


    :code:`-lut <w1>:<w2>` ::

            generate netlist using luts of (max) the specified width <w2>. All
            luts with width <= <w1> have constant cost. for luts larger than <w1>
            the area cost doubles with each additional input bit. the delay cost
            is still constant for all lut widths.


    :code:`-lut <file>` ::

            pass this file with lut library to ABC.


    :code:`-luts <cost1>,<cost2>,<cost3>,<sizeN>:<cost4-N>,..` ::

            generate netlist using luts. Use the specified costs for luts with 1,
            2, 3, .. inputs.


    :code:`-maxlut <width>` ::

            when auto-generating the lut library, discard all luts equal to or
            greater than this size (applicable when neither -lut nor -luts is
            specified).


    :code:`-dff` ::

            also pass $_DFF_[NP]_ cells through to ABC. modules with many clock
            domains are supported and automatically partitioned by ABC.


    :code:`-nocleanup` ::

            when this option is used, the temporary files created by this pass
            are not removed. this is useful for debugging.


    :code:`-showtmp` ::

            print the temp dir name in log. usually this is suppressed so that the
            command output is identical across runs.


    :code:`-box <file>` ::

            pass this file with box library to ABC.


    ::

        Note that this is a logic optimization pass within Yosys that is calling ABC
        internally. This is not going to "run ABC on your design". It will instead run
        ABC on logic snippets extracted from your design. You will not get any useful
        output when passing an ABC script that writes a file. Instead write your full
        design as an XAIGER file with `write_xaiger' and then load that into ABC
        externally if you want to use ABC to convert your design into another format.

        [1] http://www.eecs.berkeley.edu/~alanmi/abc/


            check:
                abc9_ops -check [-dff]    (option if -dff)

            map:
                abc9_ops -prep_hier [-dff]    (option if -dff)
                scc -specify -set_attr abc9_scc_id {}
                abc9_ops -prep_bypass [-prep_dff]    (option if -dff)
                design -stash $abc9
                design -load $abc9_map
                proc
                wbflip
                techmap -wb -map %$abc9 -map +/techmap.v A:abc9_flop
                opt -nodffe -nosdff
                abc9_ops -prep_dff_submod                                                     (only if -dff)
                setattr -set submod "$abc9_flop" t:$_DFF_?_ %ci* %co* t:$_DFF_?_ %d           (only if -dff)
                submod                                                                        (only if -dff)
                setattr -mod -set whitebox 1 -set abc9_flop 1 -set abc9_box 1 *_$abc9_flop    (only if -dff)
                foreach module in design
                    rename <module-name>_$abc9_flop _TECHMAP_REPLACE_                         (only if -dff)
                abc9_ops -prep_dff_unmap                                                      (only if -dff)
                design -copy-to $abc9 =*_$abc9_flop                                           (only if -dff)
                delete =*_$abc9_flop                                                          (only if -dff)
                design -stash $abc9_map
                design -load $abc9
                design -delete $abc9
                techmap -wb -max_iter 1 -map %$abc9_map -map +/abc9_map.v [-D DFF]    (option if -dff)
                design -delete $abc9_map

            pre:
                read_verilog -icells -lib -specify +/abc9_model.v
                abc9_ops -break_scc -prep_delays -prep_xaiger [-dff]    (option for -dff)
                abc9_ops -prep_lut <maxlut>    (skip if -lut or -luts)
                abc9_ops -prep_box    (skip if -box)
                design -stash $abc9
                design -load $abc9_holes
                techmap -wb -map %$abc9 -map +/techmap.v
                opt -purge
                aigmap
                design -stash $abc9_holes
                design -load $abc9
                design -delete $abc9

            exe:
                aigmap
                foreach module in selection
                    abc9_ops -write_lut <abc-temp-dir>/input.lut    (skip if '-lut' or '-luts')
                    abc9_ops -write_box <abc-temp-dir>/input.box    (skip if '-box')
                    write_xaiger -map <abc-temp-dir>/input.sym [-dff] <abc-temp-dir>/input.xaig
                    abc9_exe [options] -cwd <abc-temp-dir> -lut [<abc-temp-dir>/input.lut] -box [<abc-temp-dir>/input.box]
                    read_aiger -xaiger -wideports -module_name <module-name>$abc9 -map <abc-temp-dir>/input.sym <abc-temp-dir>/output.aig
                    abc9_ops -reintegrate [-dff]

            unmap:
                techmap -wb -map %$abc9_unmap -map +/abc9_unmap.v
                design -delete $abc9_unmap
                design -delete $abc9_holes
                delete =*_$abc9_byp
                setattr -mod -unset abc9_box_id

.. only:: latex

    ::

        
            abc9 [options] [selection]
        
        This script pass performs a sequence of commands to facilitate the use of the
        ABC tool [1] for technology mapping of the current design to a target FPGA
        architecture. Only fully-selected modules are supported.
        
            -run <from_label>:<to_label>
                only run the commands between the labels (see below). an empty
                from label is synonymous to 'begin', and empty to label is
                synonymous to the end of the command list.
        
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
                  &scorr; &sweep; &dc2; &dch -f; &ps; &if {C} {W} {D} {R} -v; &mfs
        
            -fast
                use different default scripts that are slightly faster (at the cost
                of output quality):
                  &if {C} {W} {D} {R} -v
        
            -D <picoseconds>
                set delay target. the string {D} in the default scripts above is
                replaced by this option when used, and an empty string otherwise
                (indicating best possible delay).
        
            -lut <width>
                generate netlist using luts of (max) the specified width.
        
            -lut <w1>:<w2>
                generate netlist using luts of (max) the specified width <w2>. All
                luts with width <= <w1> have constant cost. for luts larger than <w1>
                the area cost doubles with each additional input bit. the delay cost
                is still constant for all lut widths.
        
            -lut <file>
                pass this file with lut library to ABC.
        
            -luts <cost1>,<cost2>,<cost3>,<sizeN>:<cost4-N>,..
                generate netlist using luts. Use the specified costs for luts with 1,
                2, 3, .. inputs.
        
            -maxlut <width>
                when auto-generating the lut library, discard all luts equal to or
                greater than this size (applicable when neither -lut nor -luts is
                specified).
        
            -dff
                also pass $_DFF_[NP]_ cells through to ABC. modules with many clock
                domains are supported and automatically partitioned by ABC.
        
            -nocleanup
                when this option is used, the temporary files created by this pass
                are not removed. this is useful for debugging.
        
            -showtmp
                print the temp dir name in log. usually this is suppressed so that the
                command output is identical across runs.
        
            -box <file>
                pass this file with box library to ABC.
        
        Note that this is a logic optimization pass within Yosys that is calling ABC
        internally. This is not going to "run ABC on your design". It will instead run
        ABC on logic snippets extracted from your design. You will not get any useful
        output when passing an ABC script that writes a file. Instead write your full
        design as an XAIGER file with `write_xaiger' and then load that into ABC
        externally if you want to use ABC to convert your design into another format.
        
        [1] http://www.eecs.berkeley.edu/~alanmi/abc/
        
        
            check:
                abc9_ops -check [-dff]    (option if -dff)
        
            map:
                abc9_ops -prep_hier [-dff]    (option if -dff)
                scc -specify -set_attr abc9_scc_id {}
                abc9_ops -prep_bypass [-prep_dff]    (option if -dff)
                design -stash $abc9
                design -load $abc9_map
                proc
                wbflip
                techmap -wb -map %$abc9 -map +/techmap.v A:abc9_flop
                opt -nodffe -nosdff
                abc9_ops -prep_dff_submod                                                     (only if -dff)
                setattr -set submod "$abc9_flop" t:$_DFF_?_ %ci* %co* t:$_DFF_?_ %d           (only if -dff)
                submod                                                                        (only if -dff)
                setattr -mod -set whitebox 1 -set abc9_flop 1 -set abc9_box 1 *_$abc9_flop    (only if -dff)
                foreach module in design
                    rename <module-name>_$abc9_flop _TECHMAP_REPLACE_                         (only if -dff)
                abc9_ops -prep_dff_unmap                                                      (only if -dff)
                design -copy-to $abc9 =*_$abc9_flop                                           (only if -dff)
                delete =*_$abc9_flop                                                          (only if -dff)
                design -stash $abc9_map
                design -load $abc9
                design -delete $abc9
                techmap -wb -max_iter 1 -map %$abc9_map -map +/abc9_map.v [-D DFF]    (option if -dff)
                design -delete $abc9_map
        
            pre:
                read_verilog -icells -lib -specify +/abc9_model.v
                abc9_ops -break_scc -prep_delays -prep_xaiger [-dff]    (option for -dff)
                abc9_ops -prep_lut <maxlut>    (skip if -lut or -luts)
                abc9_ops -prep_box    (skip if -box)
                design -stash $abc9
                design -load $abc9_holes
                techmap -wb -map %$abc9 -map +/techmap.v
                opt -purge
                aigmap
                design -stash $abc9_holes
                design -load $abc9
                design -delete $abc9
        
            exe:
                aigmap
                foreach module in selection
                    abc9_ops -write_lut <abc-temp-dir>/input.lut    (skip if '-lut' or '-luts')
                    abc9_ops -write_box <abc-temp-dir>/input.box    (skip if '-box')
                    write_xaiger -map <abc-temp-dir>/input.sym [-dff] <abc-temp-dir>/input.xaig
                    abc9_exe [options] -cwd <abc-temp-dir> -lut [<abc-temp-dir>/input.lut] -box [<abc-temp-dir>/input.box]
                    read_aiger -xaiger -wideports -module_name <module-name>$abc9 -map <abc-temp-dir>/input.sym <abc-temp-dir>/output.aig
                    abc9_ops -reintegrate [-dff]
        
            unmap:
                techmap -wb -map %$abc9_unmap -map +/abc9_unmap.v
                design -delete $abc9_unmap
                design -delete $abc9_holes
                delete =*_$abc9_byp
                setattr -mod -unset abc9_box_id
        
