=====================================================
select - modify and view the list of selected objects
=====================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: select
    :title: modify and view the list of selected objects



    .. code:: yoscrypt

        select [ -add | -del | -set <name> ] {-read <filename> | <selection>}

   
    .. code:: yoscrypt

        select [ -unset <name> ]

   
    .. code:: yoscrypt

        select [ <assert_option> ] {-read <filename> | <selection>}

   
    .. code:: yoscrypt

        select [ -list | -write <filename> | -count | -clear ]

   
    .. code:: yoscrypt

        select -module <modname>

    ::

        Most commands use the list of currently selected objects to determine which part
        of the design to operate on. This command can be used to modify and view this
        list of selected objects.

        Note that many commands support an optional [selection] argument that can be
        used to override the global selection for the command. The syntax of this
        optional argument is identical to the syntax of the <selection> argument
        described here.


    .. code:: yoscrypt

        -add, -del

    ::

            add or remove the given objects to the current selection.
            without this options the current selection is replaced.


    .. code:: yoscrypt

        -set <name>

    ::

            do not modify the current selection. instead save the new selection
            under the given name (see @<name> below). to save the current selection,
            use "select -set <name> %"


    .. code:: yoscrypt

        -unset <name>

    ::

            do not modify the current selection. instead remove a previously saved
            selection under the given name (see @<name> below).


    .. code:: yoscrypt

        -assert-none

    ::

            do not modify the current selection. instead assert that the given
            selection is empty. i.e. produce an error if any object or module
            matching the selection is found.


    .. code:: yoscrypt

        -assert-any

    ::

            do not modify the current selection. instead assert that the given
            selection is non-empty. i.e. produce an error if no object or module
            matching the selection is found.


    .. code:: yoscrypt

        -assert-mod-count N

    ::

            do not modify the current selection. instead assert that the given
            selection contains exactly N modules (partially or fully selected).


    .. code:: yoscrypt

        -assert-count N

    ::

            do not modify the current selection. instead assert that the given
            selection contains exactly N objects.


    .. code:: yoscrypt

        -assert-max N

    ::

            do not modify the current selection. instead assert that the given
            selection contains less than or exactly N objects.


    .. code:: yoscrypt

        -assert-min N

    ::

            do not modify the current selection. instead assert that the given
            selection contains at least N objects.


    .. code:: yoscrypt

        -list

    ::

            list all objects in the current selection


    .. code:: yoscrypt

        -write <filename>

    ::

            like -list but write the output to the specified file


    .. code:: yoscrypt

        -read <filename>

    ::

            read the specified file (written by -write)


    .. code:: yoscrypt

        -count

    ::

            count all objects in the current selection


    .. code:: yoscrypt

        -clear

    ::

            clear the current selection. this effectively selects the whole
            design. it also resets the selected module (see -module). use the
            command 'select *' to select everything but stay in the current module.


    .. code:: yoscrypt

        -none

    ::

            create an empty selection. the current module is unchanged.


    .. code:: yoscrypt

        -module <modname>

    ::

            limit the current scope to the specified module.
            the difference between this and simply selecting the module
            is that all object names are interpreted relative to this
            module after this command until the selection is cleared again.


    ::

        When this command is called without an argument, the current selection
        is displayed in a compact form (i.e. only the module name when a whole module
        is selected).

        The <selection> argument itself is a series of commands for a simple stack
        machine. Each element on the stack represents a set of selected objects.
        After this commands have been executed, the union of all remaining sets
        on the stack is computed and used as selection for the command.

        Pushing (selecting) object when not in -module mode:

            <mod_pattern>
                select the specified module(s)

            <mod_pattern>/<obj_pattern>
                select the specified object(s) from the module(s)

        Pushing (selecting) object when in -module mode:

            <obj_pattern>
                select the specified object(s) from the current module

        By default, patterns will not match black/white-box modules or their
        contents. To include such objects, prefix the pattern with '='.

        A <mod_pattern> can be a module name, wildcard expression (*, ?, [..])
        matching module names, or one of the following:

            A:<pattern>, A:<pattern>=<pattern>
                all modules with an attribute matching the given pattern
                in addition to = also <, <=, >=, and > are supported

            N:<pattern>
                all modules with a name matching the given pattern
                (i.e. 'N:' is optional as it is the default matching rule)

        An <obj_pattern> can be an object name, wildcard expression, or one of
        the following:

            w:<pattern>
                all wires with a name matching the given wildcard pattern

            i:<pattern>, o:<pattern>, x:<pattern>
                all inputs (i:), outputs (o:) or any ports (x:) with matching names

            s:<size>, s:<min>:<max>
                all wires with a matching width

            m:<pattern>
                all memories with a name matching the given pattern

            c:<pattern>
                all cells with a name matching the given pattern

            t:<pattern>
                all cells with a type matching the given pattern

            p:<pattern>
                all processes with a name matching the given pattern

            a:<pattern>
                all objects with an attribute name matching the given pattern

            a:<pattern>=<pattern>
                all objects with a matching attribute name-value-pair.
                in addition to = also <, <=, >=, and > are supported

            r:<pattern>, r:<pattern>=<pattern>
                cells with matching parameters. also with <, <=, >= and >.

            n:<pattern>
                all objects with a name matching the given pattern
                (i.e. 'n:' is optional as it is the default matching rule)

            @<name>
                push the selection saved prior with 'select -set <name> ...'

        The following actions can be performed on the top sets on the stack:

            %
                push a copy of the current selection to the stack

            %%
                replace the stack with a union of all elements on it

            %n
                replace top set with its invert

            %u
                replace the two top sets on the stack with their union

            %i
                replace the two top sets on the stack with their intersection

            %d
                pop the top set from the stack and subtract it from the new top

            %D
                like %d but swap the roles of two top sets on the stack

            %c
                create a copy of the top set from the stack and push it

            %x[<num1>|*][.<num2>][:<rule>[:<rule>..]]
                expand top set <num1> num times according to the specified rules.
                (i.e. select all cells connected to selected wires and select all
                wires connected to selected cells) The rules specify which cell
                ports to use for this. the syntax for a rule is a '-' for exclusion
                and a '+' for inclusion, followed by an optional comma separated
                list of cell types followed by an optional comma separated list of
                cell ports in square brackets. a rule can also be just a cell or wire
                name that limits the expansion (is included but does not go beyond).
                select at most <num2> objects. a warning message is printed when this
                limit is reached. When '*' is used instead of <num1> then the process
                is repeated until no further object are selected.

            %ci[<num1>|*][.<num2>][:<rule>[:<rule>..]]
            %co[<num1>|*][.<num2>][:<rule>[:<rule>..]]
                similar to %x, but only select input (%ci) or output cones (%co)

            %xe[...] %cie[...] %coe
                like %x, %ci, and %co but only consider combinatorial cells

            %a
                expand top set by selecting all wires that are (at least in part)
                aliases for selected wires.

            %s
                expand top set by adding all modules that implement cells in selected
                modules

            %m
                expand top set by selecting all modules that contain selected objects

            %M
                select modules that implement selected cells

            %C
                select cells that implement selected modules

            %R[<num>]
                select <num> random objects from top selection (default 1)

        Example: the following command selects all wires that are connected to a
        'GATE' input of a 'SWITCH' cell:

            select */t:SWITCH %x:+[GATE] */t:SWITCH %d

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            select [ -add | -del | -set <name> ] {-read <filename> | <selection>}
            select [ -unset <name> ]
            select [ <assert_option> ] {-read <filename> | <selection>}
            select [ -list | -write <filename> | -count | -clear ]
            select -module <modname>
        
        Most commands use the list of currently selected objects to determine which part
        of the design to operate on. This command can be used to modify and view this
        list of selected objects.
        
        Note that many commands support an optional [selection] argument that can be
        used to override the global selection for the command. The syntax of this
        optional argument is identical to the syntax of the <selection> argument
        described here.
        
            -add, -del
                add or remove the given objects to the current selection.
                without this options the current selection is replaced.
        
            -set <name>
                do not modify the current selection. instead save the new selection
                under the given name (see @<name> below). to save the current selection,
                use "select -set <name> %"
        
            -unset <name>
                do not modify the current selection. instead remove a previously saved
                selection under the given name (see @<name> below).
        
            -assert-none
                do not modify the current selection. instead assert that the given
                selection is empty. i.e. produce an error if any object or module
                matching the selection is found.
        
            -assert-any
                do not modify the current selection. instead assert that the given
                selection is non-empty. i.e. produce an error if no object or module
                matching the selection is found.
        
            -assert-mod-count N
                do not modify the current selection. instead assert that the given
                selection contains exactly N modules (partially or fully selected).
        
            -assert-count N
                do not modify the current selection. instead assert that the given
                selection contains exactly N objects.
        
            -assert-max N
                do not modify the current selection. instead assert that the given
                selection contains less than or exactly N objects.
        
            -assert-min N
                do not modify the current selection. instead assert that the given
                selection contains at least N objects.
        
            -list
                list all objects in the current selection
        
            -write <filename>
                like -list but write the output to the specified file
        
            -read <filename>
                read the specified file (written by -write)
        
            -count
                count all objects in the current selection
        
            -clear
                clear the current selection. this effectively selects the whole
                design. it also resets the selected module (see -module). use the
                command 'select *' to select everything but stay in the current module.
        
            -none
                create an empty selection. the current module is unchanged.
        
            -module <modname>
                limit the current scope to the specified module.
                the difference between this and simply selecting the module
                is that all object names are interpreted relative to this
                module after this command until the selection is cleared again.
        
        When this command is called without an argument, the current selection
        is displayed in a compact form (i.e. only the module name when a whole module
        is selected).
        
        The <selection> argument itself is a series of commands for a simple stack
        machine. Each element on the stack represents a set of selected objects.
        After this commands have been executed, the union of all remaining sets
        on the stack is computed and used as selection for the command.
        
        Pushing (selecting) object when not in -module mode:
        
            <mod_pattern>
                select the specified module(s)
        
            <mod_pattern>/<obj_pattern>
                select the specified object(s) from the module(s)
        
        Pushing (selecting) object when in -module mode:
        
            <obj_pattern>
                select the specified object(s) from the current module
        
        By default, patterns will not match black/white-box modules or their
        contents. To include such objects, prefix the pattern with '='.
        
        A <mod_pattern> can be a module name, wildcard expression (*, ?, [..])
        matching module names, or one of the following:
        
            A:<pattern>, A:<pattern>=<pattern>
                all modules with an attribute matching the given pattern
                in addition to = also <, <=, >=, and > are supported
        
            N:<pattern>
                all modules with a name matching the given pattern
                (i.e. 'N:' is optional as it is the default matching rule)
        
        An <obj_pattern> can be an object name, wildcard expression, or one of
        the following:
        
            w:<pattern>
                all wires with a name matching the given wildcard pattern
        
            i:<pattern>, o:<pattern>, x:<pattern>
                all inputs (i:), outputs (o:) or any ports (x:) with matching names
        
            s:<size>, s:<min>:<max>
                all wires with a matching width
        
            m:<pattern>
                all memories with a name matching the given pattern
        
            c:<pattern>
                all cells with a name matching the given pattern
        
            t:<pattern>
                all cells with a type matching the given pattern
        
            p:<pattern>
                all processes with a name matching the given pattern
        
            a:<pattern>
                all objects with an attribute name matching the given pattern
        
            a:<pattern>=<pattern>
                all objects with a matching attribute name-value-pair.
                in addition to = also <, <=, >=, and > are supported
        
            r:<pattern>, r:<pattern>=<pattern>
                cells with matching parameters. also with <, <=, >= and >.
        
            n:<pattern>
                all objects with a name matching the given pattern
                (i.e. 'n:' is optional as it is the default matching rule)
        
            @<name>
                push the selection saved prior with 'select -set <name> ...'
        
        The following actions can be performed on the top sets on the stack:
        
            %
                push a copy of the current selection to the stack
        
            %%
                replace the stack with a union of all elements on it
        
            %n
                replace top set with its invert
        
            %u
                replace the two top sets on the stack with their union
        
            %i
                replace the two top sets on the stack with their intersection
        
            %d
                pop the top set from the stack and subtract it from the new top
        
            %D
                like %d but swap the roles of two top sets on the stack
        
            %c
                create a copy of the top set from the stack and push it
        
            %x[<num1>|*][.<num2>][:<rule>[:<rule>..]]
                expand top set <num1> num times according to the specified rules.
                (i.e. select all cells connected to selected wires and select all
                wires connected to selected cells) The rules specify which cell
                ports to use for this. the syntax for a rule is a '-' for exclusion
                and a '+' for inclusion, followed by an optional comma separated
                list of cell types followed by an optional comma separated list of
                cell ports in square brackets. a rule can also be just a cell or wire
                name that limits the expansion (is included but does not go beyond).
                select at most <num2> objects. a warning message is printed when this
                limit is reached. When '*' is used instead of <num1> then the process
                is repeated until no further object are selected.
        
            %ci[<num1>|*][.<num2>][:<rule>[:<rule>..]]
            %co[<num1>|*][.<num2>][:<rule>[:<rule>..]]
                similar to %x, but only select input (%ci) or output cones (%co)
        
            %xe[...] %cie[...] %coe
                like %x, %ci, and %co but only consider combinatorial cells
        
            %a
                expand top set by selecting all wires that are (at least in part)
                aliases for selected wires.
        
            %s
                expand top set by adding all modules that implement cells in selected
                modules
        
            %m
                expand top set by selecting all modules that contain selected objects
        
            %M
                select modules that implement selected cells
        
            %C
                select cells that implement selected modules
        
            %R[<num>]
                select <num> random objects from top selection (default 1)
        
        Example: the following command selects all wires that are connected to a
        'GATE' input of a 'SWITCH' cell:
        
            select */t:SWITCH %x:+[GATE] */t:SWITCH %d
        
