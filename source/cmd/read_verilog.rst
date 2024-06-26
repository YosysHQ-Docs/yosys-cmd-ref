=============================================
read_verilog - read modules from Verilog file
=============================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: read_verilog
    :title: read modules from Verilog file



    .. code:: yoscrypt

        read_verilog [options] [filename]

    ::

        Load modules from a Verilog file to the current design. A large subset of
        Verilog-2005 is supported.


    .. code:: yoscrypt

        -sv

    ::

            enable support for SystemVerilog features. (only a small subset
            of SystemVerilog is supported)


    .. code:: yoscrypt

        -formal

    ::

            enable support for SystemVerilog assertions and some Yosys extensions
            replace the implicit -D SYNTHESIS with -D FORMAL


    .. code:: yoscrypt

        -nosynthesis

    ::

            don't add implicit -D SYNTHESIS


    .. code:: yoscrypt

        -noassert

    ::

            ignore assert() statements


    .. code:: yoscrypt

        -noassume

    ::

            ignore assume() statements


    .. code:: yoscrypt

        -norestrict

    ::

            ignore restrict() statements


    .. code:: yoscrypt

        -assume-asserts

    ::

            treat all assert() statements like assume() statements


    .. code:: yoscrypt

        -assert-assumes

    ::

            treat all assume() statements like assert() statements


    .. code:: yoscrypt

        -nodisplay

    ::

            suppress output from display system tasks ($display et. al).
            This does not affect the output from a later 'sim' command.


    .. code:: yoscrypt

        -debug

    ::

            alias for -dump_ast1 -dump_ast2 -dump_vlog1 -dump_vlog2 -yydebug


    .. code:: yoscrypt

        -dump_ast1

    ::

            dump abstract syntax tree (before simplification)


    .. code:: yoscrypt

        -dump_ast2

    ::

            dump abstract syntax tree (after simplification)


    .. code:: yoscrypt

        -no_dump_ptr

    ::

            do not include hex memory addresses in dump (easier to diff dumps)


    .. code:: yoscrypt

        -dump_vlog1

    ::

            dump ast as Verilog code (before simplification)


    .. code:: yoscrypt

        -dump_vlog2

    ::

            dump ast as Verilog code (after simplification)


    .. code:: yoscrypt

        -dump_rtlil

    ::

            dump generated RTLIL netlist


    .. code:: yoscrypt

        -yydebug

    ::

            enable parser debug output


    .. code:: yoscrypt

        -nolatches

    ::

            usually latches are synthesized into logic loops
            this option prohibits this and sets the output to 'x'
            in what would be the latches hold condition

            this behavior can also be achieved by setting the
            'nolatches' attribute on the respective module or
            always block.


    .. code:: yoscrypt

        -nomem2reg

    ::

            under certain conditions memories are converted to registers
            early during simplification to ensure correct handling of
            complex corner cases. this option disables this behavior.

            this can also be achieved by setting the 'nomem2reg'
            attribute on the respective module or register.

            This is potentially dangerous. Usually the front-end has good
            reasons for converting an array to a list of registers.
            Prohibiting this step will likely result in incorrect synthesis
            results.


    .. code:: yoscrypt

        -mem2reg

    ::

            always convert memories to registers. this can also be
            achieved by setting the 'mem2reg' attribute on the respective
            module or register.


    .. code:: yoscrypt

        -nomeminit

    ::

            do not infer $meminit cells and instead convert initialized
            memories to registers directly in the front-end.


    .. code:: yoscrypt

        -ppdump

    ::

            dump Verilog code after pre-processor


    .. code:: yoscrypt

        -nopp

    ::

            do not run the pre-processor


    .. code:: yoscrypt

        -nodpi

    ::

            disable DPI-C support


    .. code:: yoscrypt

        -noblackbox

    ::

            do not automatically add a (* blackbox *) attribute to an
            empty module.


    .. code:: yoscrypt

        -lib

    ::

            only create empty blackbox modules. This implies -DBLACKBOX.
            modules with the (* whitebox *) attribute will be preserved.
            (* lib_whitebox *) will be treated like (* whitebox *).


    .. code:: yoscrypt

        -nowb

    ::

            delete (* whitebox *) and (* lib_whitebox *) attributes from
            all modules.


    .. code:: yoscrypt

        -specify

    ::

            parse and import specify blocks


    .. code:: yoscrypt

        -noopt

    ::

            don't perform basic optimizations (such as const folding) in the
            high-level front-end.


    .. code:: yoscrypt

        -icells

    ::

            interpret cell types starting with '$' as internal cell types


    .. code:: yoscrypt

        -pwires

    ::

            add a wire for each module parameter


    .. code:: yoscrypt

        -nooverwrite

    ::

            ignore re-definitions of modules. (the default behavior is to
            create an error message if the existing module is not a black box
            module, and overwrite the existing module otherwise.)


    .. code:: yoscrypt

        -overwrite

    ::

            overwrite existing modules with the same name


    .. code:: yoscrypt

        -defer

    ::

            only read the abstract syntax tree and defer actual compilation
            to a later 'hierarchy' command. Useful in cases where the default
            parameters of modules yield invalid or not synthesizable code.


    .. code:: yoscrypt

        -noautowire

    ::

            make the default of `default_nettype be "none" instead of "wire".


    .. code:: yoscrypt

        -setattr <attribute_name>

    ::

            set the specified attribute (to the value 1) on all loaded modules


    .. code:: yoscrypt

        -Dname[=definition]

    ::

            define the preprocessor symbol 'name' and set its optional value
            'definition'


    .. code:: yoscrypt

        -Idir

    ::

            add 'dir' to the directories which are used when searching include
            files


    ::

        The command 'verilog_defaults' can be used to register default options for
        subsequent calls to 'read_verilog'.

        Note that the Verilog frontend does a pretty good job of processing valid
        verilog input, but has not very good error reporting. It generally is
        recommended to use a simulator (for example Icarus Verilog) for checking
        the syntax of the code, rather than to rely on read_verilog for that.

        Depending on if read_verilog is run in -formal mode, either the macro
        SYNTHESIS or FORMAL is defined automatically, unless -nosynthesis is used.
        In addition, read_verilog always defines the macro YOSYS.

        See the Yosys README file for a list of non-standard Verilog features
        supported by the Yosys Verilog front-end.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            read_verilog [options] [filename]
        
        Load modules from a Verilog file to the current design. A large subset of
        Verilog-2005 is supported.
        
            -sv
                enable support for SystemVerilog features. (only a small subset
                of SystemVerilog is supported)
        
            -formal
                enable support for SystemVerilog assertions and some Yosys extensions
                replace the implicit -D SYNTHESIS with -D FORMAL
        
            -nosynthesis
                don't add implicit -D SYNTHESIS
        
            -noassert
                ignore assert() statements
        
            -noassume
                ignore assume() statements
        
            -norestrict
                ignore restrict() statements
        
            -assume-asserts
                treat all assert() statements like assume() statements
        
            -assert-assumes
                treat all assume() statements like assert() statements
        
            -nodisplay
                suppress output from display system tasks ($display et. al).
                This does not affect the output from a later 'sim' command.
        
            -debug
                alias for -dump_ast1 -dump_ast2 -dump_vlog1 -dump_vlog2 -yydebug
        
            -dump_ast1
                dump abstract syntax tree (before simplification)
        
            -dump_ast2
                dump abstract syntax tree (after simplification)
        
            -no_dump_ptr
                do not include hex memory addresses in dump (easier to diff dumps)
        
            -dump_vlog1
                dump ast as Verilog code (before simplification)
        
            -dump_vlog2
                dump ast as Verilog code (after simplification)
        
            -dump_rtlil
                dump generated RTLIL netlist
        
            -yydebug
                enable parser debug output
        
            -nolatches
                usually latches are synthesized into logic loops
                this option prohibits this and sets the output to 'x'
                in what would be the latches hold condition
        
                this behavior can also be achieved by setting the
                'nolatches' attribute on the respective module or
                always block.
        
            -nomem2reg
                under certain conditions memories are converted to registers
                early during simplification to ensure correct handling of
                complex corner cases. this option disables this behavior.
        
                this can also be achieved by setting the 'nomem2reg'
                attribute on the respective module or register.
        
                This is potentially dangerous. Usually the front-end has good
                reasons for converting an array to a list of registers.
                Prohibiting this step will likely result in incorrect synthesis
                results.
        
            -mem2reg
                always convert memories to registers. this can also be
                achieved by setting the 'mem2reg' attribute on the respective
                module or register.
        
            -nomeminit
                do not infer $meminit cells and instead convert initialized
                memories to registers directly in the front-end.
        
            -ppdump
                dump Verilog code after pre-processor
        
            -nopp
                do not run the pre-processor
        
            -nodpi
                disable DPI-C support
        
            -noblackbox
                do not automatically add a (* blackbox *) attribute to an
                empty module.
        
            -lib
                only create empty blackbox modules. This implies -DBLACKBOX.
                modules with the (* whitebox *) attribute will be preserved.
                (* lib_whitebox *) will be treated like (* whitebox *).
        
            -nowb
                delete (* whitebox *) and (* lib_whitebox *) attributes from
                all modules.
        
            -specify
                parse and import specify blocks
        
            -noopt
                don't perform basic optimizations (such as const folding) in the
                high-level front-end.
        
            -icells
                interpret cell types starting with '$' as internal cell types
        
            -pwires
                add a wire for each module parameter
        
            -nooverwrite
                ignore re-definitions of modules. (the default behavior is to
                create an error message if the existing module is not a black box
                module, and overwrite the existing module otherwise.)
        
            -overwrite
                overwrite existing modules with the same name
        
            -defer
                only read the abstract syntax tree and defer actual compilation
                to a later 'hierarchy' command. Useful in cases where the default
                parameters of modules yield invalid or not synthesizable code.
        
            -noautowire
                make the default of `default_nettype be "none" instead of "wire".
        
            -setattr <attribute_name>
                set the specified attribute (to the value 1) on all loaded modules
        
            -Dname[=definition]
                define the preprocessor symbol 'name' and set its optional value
                'definition'
        
            -Idir
                add 'dir' to the directories which are used when searching include
                files
        
        The command 'verilog_defaults' can be used to register default options for
        subsequent calls to 'read_verilog'.
        
        Note that the Verilog frontend does a pretty good job of processing valid
        verilog input, but has not very good error reporting. It generally is
        recommended to use a simulator (for example Icarus Verilog) for checking
        the syntax of the code, rather than to rely on read_verilog for that.
        
        Depending on if read_verilog is run in -formal mode, either the macro
        SYNTHESIS or FORMAL is defined automatically, unless -nosynthesis is used.
        In addition, read_verilog always defines the macro YOSYS.
        
        See the Yosys README file for a list of non-standard Verilog features
        supported by the Yosys Verilog front-end.
        
