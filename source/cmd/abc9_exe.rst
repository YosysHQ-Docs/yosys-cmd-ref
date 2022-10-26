==========================================
abc9_exe - use ABC9 for technology mapping
==========================================

.. only:: html

    :code:`yosys> help abc9_exe`
    ----------------------------------------------------------------------------


    :code:`abc9_exe [options]` ::

        This pass uses the ABC tool [1] for technology mapping of the top module
        (according to the (* top *) attribute or if only one module is currently
        selected) to a target FPGA architecture.


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


    :code:`-showtmp` ::

            print the temp dir name in log. usually this is suppressed so that the
            command output is identical across runs.


    :code:`-box <file>` ::

            pass this file with box library to ABC.


    :code:`-cwd <dir>` ::

            use this as the current working directory, inside which the 'input.xaig'
            file is expected. temporary files will be created in this directory, and
            the mapped result will be written to 'output.aig'.


    ::

        Note that this is a logic optimization pass within Yosys that is calling ABC
        internally. This is not going to "run ABC on your design". It will instead run
        ABC on logic snippets extracted from your design. You will not get any useful
        output when passing an ABC script that writes a file. Instead write your full
        design as BLIF file with write_blif and then load that into ABC externally if
        you want to use ABC to convert your design into another format.

        [1] http://www.eecs.berkeley.edu/~alanmi/abc/

.. only:: latex

    ::

        
            abc9_exe [options]
        
         
        This pass uses the ABC tool [1] for technology mapping of the top module
        (according to the (* top *) attribute or if only one module is currently
        selected) to a target FPGA architecture.
        
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
        
            -showtmp
                print the temp dir name in log. usually this is suppressed so that the
                command output is identical across runs.
        
            -box <file>
                pass this file with box library to ABC.
        
            -cwd <dir>
                use this as the current working directory, inside which the 'input.xaig'
                file is expected. temporary files will be created in this directory, and
                the mapped result will be written to 'output.aig'.
        
        Note that this is a logic optimization pass within Yosys that is calling ABC
        internally. This is not going to "run ABC on your design". It will instead run
        ABC on logic snippets extracted from your design. You will not get any useful
        output when passing an ABC script that writes a file. Instead write your full
        design as BLIF file with write_blif and then load that into ABC externally if
        you want to use ABC to convert your design into another format.
        
        [1] http://www.eecs.berkeley.edu/~alanmi/abc/
        
