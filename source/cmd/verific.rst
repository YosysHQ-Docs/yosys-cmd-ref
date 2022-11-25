=====================================================
verific - load Verilog and VHDL designs using Verific
=====================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help verific`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        verific {-vlog95|-vlog2k|-sv2005|-sv2009|-sv2012|-sv} <verilog-file>..

    ::

        Load the specified Verilog/SystemVerilog files into Verific.

        All files specified in one call to this command are one compilation unit.
        Files passed to different calls to this command are treated as belonging to
        different compilation units.

        Additional -D<macro>[=<value>] options may be added after the option indicating
        the language version (and before file names) to set additional verilog defines.
        The macros YOSYS, SYNTHESIS, and VERIFIC are defined implicitly.


            verific -formal <verilog-file>..

        Like -sv, but define FORMAL instead of SYNTHESIS.


            verific {-vhdl87|-vhdl93|-vhdl2k|-vhdl2008|-vhdl} <vhdl-file>..

        Load the specified VHDL files into Verific.


            verific {-edif} <edif-file>..

        Load the specified EDIF files into Verific.


            verific {-liberty} <liberty-file>..

        Load the specified Liberty files into Verific.
        Default library when -work is not present is one specified in liberty file.
        To use from SystemVerilog or VHDL use -L to specify liberty library.
            -lib
                only create empty blackbox modules


            verific {-f|-F} [-vlog95|-vlog2k|-sv2005|-sv2009|
                             -sv2012|-sv|-formal] <command-file>

        Load and execute the specified command file.
        Override verilog parsing mode can be set.
        The macros YOSYS, SYNTHESIS/FORMAL, and VERIFIC are defined implicitly.

        Command file parser supports following commands in file:
            +define+<MACRO>=<VALUE> - defines macro
            -u                      - upper case all identifier (makes Verilog parser
                                      case insensitive)
            -v <filepath>           - register library name (file)
            -y <filepath>           - register library name (directory)
            +incdir+<filepath>      - specify include dir
            +libext+<filepath>      - specify library extension
            +liborder+<id>          - add library in ordered list
            +librescan              - unresolved modules will be always searched
                                      starting with the first library specified
                                      by -y/-v options.
            -f/-file <filepath>     - nested -f option
            -F <filepath>           - nested -F option (relative path)
            parse files:
                <filepath>
                +systemverilogext+<filepath>
                +verilog1995ext+<filepath>
                +verilog2001ext+<filepath>

            analysis mode:
                -ams
                +v2k
                -sverilog


            verific [-work <libname>] {-sv|-vhdl|...} <hdl-file>

        Load the specified Verilog/SystemVerilog/VHDL file into the specified library.
        (default library when -work is not present: "work")


            verific [-L <libname>] {-sv|-vhdl|...} <hdl-file>

        Look up external definitions in the specified library.
        (-L may be used more than once)


            verific -vlog-incdir <directory>..

        Add Verilog include directories.


            verific -vlog-libdir <directory>..

        Add Verilog library directories. Verific will search in this directories to
        find undefined modules.


            verific -vlog-libext <extension>..

        Add Verilog library extensions, used when searching in library directories.


            verific -vlog-define <macro>[=<value>]..

        Add Verilog defines.


            verific -vlog-undef <macro>..

        Remove Verilog defines previously set with -vlog-define.


            verific -set-error <msg_id>..
            verific -set-warning <msg_id>..
            verific -set-info <msg_id>..
            verific -set-ignore <msg_id>..

        Set message severity. <msg_id> is the string in square brackets when a message
        is printed, such as VERI-1209.


            verific -import [options] <top>..

        Elaborate the design for the specified top modules or configurations, import to
        Yosys and reset the internal state of Verific.

        Import options:

          -all
            Elaborate all modules, not just the hierarchy below the given top
            modules. With this option the list of modules to import is optional.

          -gates
            Create a gate-level netlist.

          -flatten
            Flatten the design in Verific before importing.

          -extnets
            Resolve references to external nets by adding module ports as needed.

          -autocover
            Generate automatic cover statements for all asserts

          -fullinit
            Keep all register initializations, even those for non-FF registers.

          -cells
            Import all cell definitions from Verific loaded libraries even if they are
            unused in design. Useful with "-edif" and "-liberty" option.

          -chparam name value 
            Elaborate the specified top modules (all modules when -all given) using
            this parameter value. Modules on which this parameter does not exist will
            cause Verific to produce a VERI-1928 or VHDL-1676 message. This option
            can be specified multiple times to override multiple parameters.
            String values must be passed in double quotes (").

          -v, -vv
            Verbose log messages. (-vv is even more verbose than -v.)

          -pp <filename>
            Pretty print design after elaboration to specified file.

        The following additional import options are useful for debugging the Verific
        bindings (for Yosys and/or Verific developers):

          -k
            Keep going after an unsupported verific primitive is found. The
            unsupported primitive is added as blockbox module to the design.
            This will also add all SVA related cells to the design parallel to
            the checker logic inferred by it.

          -V
            Import Verific netlist as-is without translating to Yosys cell types. 

          -nosva
            Ignore SVA properties, do not infer checker logic.

          -L <int>
            Maximum number of ctrl bits for SVA checker FSMs (default=16).

          -n
            Keep all Verific names on instances and nets. By default only
            user-declared names are preserved.

          -d <dump_file>
            Dump the Verific netlist as a verilog file.


            verific [-work <libname>] -pp [options] <filename> [<module>]..

        Pretty print design (or just module) to the specified file from the
        specified library. (default library when -work is not present: "work")

        Pretty print options:

          -verilog
            Save output for Verilog/SystemVerilog design modules (default).

          -vhdl
            Save output for VHDL design units.


            verific -cfg [<name> [<value>]]

        Get/set Verific runtime flags.


            verific [-work <libname>] -rewrite [-clear][-list] <name> [options]..

        Register rewriter for execution on elaboration step.

            -help
                Displays help for specific rewriter.

            -clear
                Remove all rewriters from list, including default rewriters.

            -list
                Displays all rewriter in list in order of execution.

            -module <module>
                Run rewriter only on specified module.

            -work <libname>
                Use verilog sources from given library.
                (default library when -work is not present: "work")

            -blacklist <filename[:lineno]>
                Do not run rewriter on modules from files that match the filename
                or filename and line number if provided in such format.
                Parameter can also contain comma separated list of file locations.

            -blfile <file>
                Do not run rewriter on locations specified in file, they can
                represent filename or filename and location in file.

            -whitelist <filename[:lineno]>
                Run rewriter on modules from files that match the filename
                or filename and line number if provided in such format.
                Parameter can also contain comma separated list of file locations.

            -wlfile <file>
                Run rewriter on locations specified in file, they can
                represent filename or filename and location in file.

        Available rewriters:
          gen-witness-covers   - Generate witness covers
          initial-assertions   - Generate initial block assertions (automatically added)


            verific [-work <libname>] -elaborate [options]..

        Execute elaboration step and all registered rewriters.

            -work <libname>
                Use verilog sources from given library.
                (default library when -work is not present: "work")

        Use YosysHQ Tabby CAD Suite if you need Yosys+Verific.
        https://www.yosyshq.com/

        Contact office@yosyshq.com for free evaluation
        binaries of YosysHQ Tabby CAD Suite.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            verific {-vlog95|-vlog2k|-sv2005|-sv2009|-sv2012|-sv} <verilog-file>..
        
        Load the specified Verilog/SystemVerilog files into Verific.
        
        All files specified in one call to this command are one compilation unit.
        Files passed to different calls to this command are treated as belonging to
        different compilation units.
        
        Additional -D<macro>[=<value>] options may be added after the option indicating
        the language version (and before file names) to set additional verilog defines.
        The macros YOSYS, SYNTHESIS, and VERIFIC are defined implicitly.
        
        
            verific -formal <verilog-file>..
        
        Like -sv, but define FORMAL instead of SYNTHESIS.
        
        
            verific {-vhdl87|-vhdl93|-vhdl2k|-vhdl2008|-vhdl} <vhdl-file>..
        
        Load the specified VHDL files into Verific.
        
        
            verific {-edif} <edif-file>..
        
        Load the specified EDIF files into Verific.
        
        
            verific {-liberty} <liberty-file>..
        
        Load the specified Liberty files into Verific.
        Default library when -work is not present is one specified in liberty file.
        To use from SystemVerilog or VHDL use -L to specify liberty library.
            -lib
                only create empty blackbox modules
        
        
            verific {-f|-F} [-vlog95|-vlog2k|-sv2005|-sv2009|
                             -sv2012|-sv|-formal] <command-file>
        
        Load and execute the specified command file.
        Override verilog parsing mode can be set.
        The macros YOSYS, SYNTHESIS/FORMAL, and VERIFIC are defined implicitly.
        
        Command file parser supports following commands in file:
            +define+<MACRO>=<VALUE> - defines macro
            -u                      - upper case all identifier (makes Verilog parser
                                      case insensitive)
            -v <filepath>           - register library name (file)
            -y <filepath>           - register library name (directory)
            +incdir+<filepath>      - specify include dir
            +libext+<filepath>      - specify library extension
            +liborder+<id>          - add library in ordered list
            +librescan              - unresolved modules will be always searched
                                      starting with the first library specified
                                      by -y/-v options.
            -f/-file <filepath>     - nested -f option
            -F <filepath>           - nested -F option (relative path)
            parse files:
                <filepath>
                +systemverilogext+<filepath>
                +verilog1995ext+<filepath>
                +verilog2001ext+<filepath>
        
            analysis mode:
                -ams
                +v2k
                -sverilog
        
        
            verific [-work <libname>] {-sv|-vhdl|...} <hdl-file>
        
        Load the specified Verilog/SystemVerilog/VHDL file into the specified library.
        (default library when -work is not present: "work")
        
        
            verific [-L <libname>] {-sv|-vhdl|...} <hdl-file>
        
        Look up external definitions in the specified library.
        (-L may be used more than once)
        
        
            verific -vlog-incdir <directory>..
        
        Add Verilog include directories.
        
        
            verific -vlog-libdir <directory>..
        
        Add Verilog library directories. Verific will search in this directories to
        find undefined modules.
        
        
            verific -vlog-libext <extension>..
        
        Add Verilog library extensions, used when searching in library directories.
        
        
            verific -vlog-define <macro>[=<value>]..
        
        Add Verilog defines.
        
        
            verific -vlog-undef <macro>..
        
        Remove Verilog defines previously set with -vlog-define.
        
        
            verific -set-error <msg_id>..
            verific -set-warning <msg_id>..
            verific -set-info <msg_id>..
            verific -set-ignore <msg_id>..
        
        Set message severity. <msg_id> is the string in square brackets when a message
        is printed, such as VERI-1209.
        
        
            verific -import [options] <top>..
        
        Elaborate the design for the specified top modules or configurations, import to
        Yosys and reset the internal state of Verific.
        
        Import options:
        
          -all
            Elaborate all modules, not just the hierarchy below the given top
            modules. With this option the list of modules to import is optional.
        
          -gates
            Create a gate-level netlist.
        
          -flatten
            Flatten the design in Verific before importing.
        
          -extnets
            Resolve references to external nets by adding module ports as needed.
        
          -autocover
            Generate automatic cover statements for all asserts
        
          -fullinit
            Keep all register initializations, even those for non-FF registers.
        
          -cells
            Import all cell definitions from Verific loaded libraries even if they are
            unused in design. Useful with "-edif" and "-liberty" option.
        
          -chparam name value 
            Elaborate the specified top modules (all modules when -all given) using
            this parameter value. Modules on which this parameter does not exist will
            cause Verific to produce a VERI-1928 or VHDL-1676 message. This option
            can be specified multiple times to override multiple parameters.
            String values must be passed in double quotes (").
        
          -v, -vv
            Verbose log messages. (-vv is even more verbose than -v.)
        
          -pp <filename>
            Pretty print design after elaboration to specified file.
        
        The following additional import options are useful for debugging the Verific
        bindings (for Yosys and/or Verific developers):
        
          -k
            Keep going after an unsupported verific primitive is found. The
            unsupported primitive is added as blockbox module to the design.
            This will also add all SVA related cells to the design parallel to
            the checker logic inferred by it.
        
          -V
            Import Verific netlist as-is without translating to Yosys cell types. 
        
          -nosva
            Ignore SVA properties, do not infer checker logic.
        
          -L <int>
            Maximum number of ctrl bits for SVA checker FSMs (default=16).
        
          -n
            Keep all Verific names on instances and nets. By default only
            user-declared names are preserved.
        
          -d <dump_file>
            Dump the Verific netlist as a verilog file.
        
        
            verific [-work <libname>] -pp [options] <filename> [<module>]..
        
        Pretty print design (or just module) to the specified file from the
        specified library. (default library when -work is not present: "work")
        
        Pretty print options:
        
          -verilog
            Save output for Verilog/SystemVerilog design modules (default).
        
          -vhdl
            Save output for VHDL design units.
        
        
            verific -cfg [<name> [<value>]]
        
        Get/set Verific runtime flags.
        
        
            verific [-work <libname>] -rewrite [-clear][-list] <name> [options]..
        
        Register rewriter for execution on elaboration step.
        
            -help
                Displays help for specific rewriter.
        
            -clear
                Remove all rewriters from list, including default rewriters.
        
            -list
                Displays all rewriter in list in order of execution.
        
            -module <module>
                Run rewriter only on specified module.
        
            -work <libname>
                Use verilog sources from given library.
                (default library when -work is not present: "work")
        
            -blacklist <filename[:lineno]>
                Do not run rewriter on modules from files that match the filename
                or filename and line number if provided in such format.
                Parameter can also contain comma separated list of file locations.
        
            -blfile <file>
                Do not run rewriter on locations specified in file, they can
                represent filename or filename and location in file.
        
            -whitelist <filename[:lineno]>
                Run rewriter on modules from files that match the filename
                or filename and line number if provided in such format.
                Parameter can also contain comma separated list of file locations.
        
            -wlfile <file>
                Run rewriter on locations specified in file, they can
                represent filename or filename and location in file.
        
        Available rewriters:
          gen-witness-covers   - Generate witness covers
          initial-assertions   - Generate initial block assertions (automatically added)
        
        
            verific [-work <libname>] -elaborate [options]..
        
        Execute elaboration step and all registered rewriters.
        
            -work <libname>
                Use verilog sources from given library.
                (default library when -work is not present: "work")
        
        Use YosysHQ Tabby CAD Suite if you need Yosys+Verific.
        https://www.yosyshq.com/
        
        Contact office@yosyshq.com for free evaluation
        binaries of YosysHQ Tabby CAD Suite.
        
