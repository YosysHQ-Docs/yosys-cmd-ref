=======================================================
hierarchy - check, expand and clean up design hierarchy
=======================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: hierarchy
    :title: check, expand and clean up design hierarchy



    .. code:: yoscrypt

        hierarchy [-check] [-top <module>]

   
    .. code:: yoscrypt

        hierarchy -generate <cell-types> <port-decls>

    ::

        In parametric designs, a module might exists in several variations with
        different parameter values. This pass looks at all modules in the current
        design and re-runs the language frontends for the parametric modules as
        needed. It also resolves assignments to wired logic data types (wand/wor),
        resolves positional module parameters, unrolls array instances, and more.


    .. code:: yoscrypt

        -check

    ::

            also check the design hierarchy. this generates an error when
            an unknown module is used as cell type.


    .. code:: yoscrypt

        -simcheck

    ::

            like -check, but also throw an error if blackbox modules are
            instantiated, and throw an error if the design has no top module.


    .. code:: yoscrypt

        -smtcheck

    ::

            like -simcheck, but allow smtlib2_module modules.


    .. code:: yoscrypt

        -purge_lib

    ::

            by default the hierarchy command will not remove library (blackbox)
            modules. use this option to also remove unused blackbox modules.


    .. code:: yoscrypt

        -libdir <directory>

    ::

            search for files named <module_name>.v in the specified directory
            for unknown modules and automatically run read_verilog for each
            unknown module.


    .. code:: yoscrypt

        -keep_positionals

    ::

            per default this pass also converts positional arguments in cells
            to arguments using port names. This option disables this behavior.


    .. code:: yoscrypt

        -keep_portwidths

    ::

            per default this pass adjusts the port width on cells that are
            module instances when the width does not match the module port. This
            option disables this behavior.


    .. code:: yoscrypt

        -nodefaults

    ::

            do not resolve input port default values


    .. code:: yoscrypt

        -nokeep_prints

    ::

            per default this pass sets the "keep" attribute on all modules
            that directly or indirectly display text on the terminal.
            This option disables this behavior.


    .. code:: yoscrypt

        -nokeep_asserts

    ::

            per default this pass sets the "keep" attribute on all modules
            that directly or indirectly contain one or more formal properties.
            This option disables this behavior.


    .. code:: yoscrypt

        -top <module>

    ::

            use the specified top module to build the design hierarchy. Modules
            outside this tree (unused modules) are removed.

            when the -top option is used, the 'top' attribute will be set on the
            specified top module. otherwise a module with the 'top' attribute set
            will implicitly be used as top module, if such a module exists.


    .. code:: yoscrypt

        -auto-top

    ::

            automatically determine the top of the design hierarchy and mark it.


    .. code:: yoscrypt

        -chparam name value

    ::

           elaborate the top module using this parameter value. Modules on which
           this parameter does not exist may cause a warning message to be output.
           This option can be specified multiple times to override multiple
           parameters. String values must be passed in double quotes (").


    ::

        In -generate mode this pass generates blackbox modules for the given cell
        types (wildcards supported). For this the design is searched for cells that
        match the given types and then the given port declarations are used to
        determine the direction of the ports. The syntax for a port declaration is:

            {i|o|io}[@<num>]:<portname>

        Input ports are specified with the 'i' prefix, output ports with the 'o'
        prefix and inout ports with the 'io' prefix. The optional <num> specifies
        the position of the port in the parameter list (needed when instantiated
        using positional arguments). When <num> is not specified, the <portname> can
        also contain wildcard characters.

        This pass ignores the current selection and always operates on all modules
        in the current design.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            hierarchy [-check] [-top <module>]
            hierarchy -generate <cell-types> <port-decls>
        
        In parametric designs, a module might exists in several variations with
        different parameter values. This pass looks at all modules in the current
        design and re-runs the language frontends for the parametric modules as
        needed. It also resolves assignments to wired logic data types (wand/wor),
        resolves positional module parameters, unrolls array instances, and more.
        
            -check
                also check the design hierarchy. this generates an error when
                an unknown module is used as cell type.
        
            -simcheck
                like -check, but also throw an error if blackbox modules are
                instantiated, and throw an error if the design has no top module.
        
            -smtcheck
                like -simcheck, but allow smtlib2_module modules.
        
            -purge_lib
                by default the hierarchy command will not remove library (blackbox)
                modules. use this option to also remove unused blackbox modules.
        
            -libdir <directory>
                search for files named <module_name>.v in the specified directory
                for unknown modules and automatically run read_verilog for each
                unknown module.
        
            -keep_positionals
                per default this pass also converts positional arguments in cells
                to arguments using port names. This option disables this behavior.
        
            -keep_portwidths
                per default this pass adjusts the port width on cells that are
                module instances when the width does not match the module port. This
                option disables this behavior.
        
            -nodefaults
                do not resolve input port default values
        
            -nokeep_prints
                per default this pass sets the "keep" attribute on all modules
                that directly or indirectly display text on the terminal.
                This option disables this behavior.
        
            -nokeep_asserts
                per default this pass sets the "keep" attribute on all modules
                that directly or indirectly contain one or more formal properties.
                This option disables this behavior.
        
            -top <module>
                use the specified top module to build the design hierarchy. Modules
                outside this tree (unused modules) are removed.
        
                when the -top option is used, the 'top' attribute will be set on the
                specified top module. otherwise a module with the 'top' attribute set
                will implicitly be used as top module, if such a module exists.
        
            -auto-top
                automatically determine the top of the design hierarchy and mark it.
        
            -chparam name value 
               elaborate the top module using this parameter value. Modules on which
               this parameter does not exist may cause a warning message to be output.
               This option can be specified multiple times to override multiple
               parameters. String values must be passed in double quotes (").
        
        In -generate mode this pass generates blackbox modules for the given cell
        types (wildcards supported). For this the design is searched for cells that
        match the given types and then the given port declarations are used to
        determine the direction of the ports. The syntax for a port declaration is:
        
            {i|o|io}[@<num>]:<portname>
        
        Input ports are specified with the 'i' prefix, output ports with the 'o'
        prefix and inout ports with the 'io' prefix. The optional <num> specifies
        the position of the port in the parameter list (needed when instantiated
        using positional arguments). When <num> is not specified, the <portname> can
        also contain wildcard characters.
        
        This pass ignores the current selection and always operates on all modules
        in the current design.
        
