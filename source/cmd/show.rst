=========================================
show - generate schematics using graphviz
=========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help show`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        show [options] [selection]

    ::

        Create a graphviz DOT file for the selected part of the design and compile it
        to a graphics file (usually SVG or PostScript).


    .. code:: yoscrypt

        -viewer <viewer>

    ::

            Run the specified command with the graphics file as parameter.
            On Windows, this pauses yosys until the viewer exits.
            Use "-viewer none" to not run any command.


    .. code:: yoscrypt

        -format <format>

    ::

            Generate a graphics file in the specified format. Use 'dot' to just
            generate a .dot file, or other <format> strings such as 'svg' or 'ps'
            to generate files in other formats (this calls the 'dot' command).


    .. code:: yoscrypt

        -lib <verilog_or_rtlil_file>

    ::

            Use the specified library file for determining whether cell ports are
            inputs or outputs. This option can be used multiple times to specify
            more than one library.

            note: in most cases it is better to load the library before calling
            show with 'read_verilog -lib <filename>'. it is also possible to
            load liberty files with 'read_liberty -lib <filename>'.


    .. code:: yoscrypt

        -prefix <prefix>

    ::

            generate <prefix>.* instead of ~/.yosys_show.*


    .. code:: yoscrypt

        -color <color> <object>

    ::

            assign the specified color to the specified object. The object can be
            a single selection wildcard expressions or a saved set of objects in
            the @<name> syntax (see "help select" for details).


    .. code:: yoscrypt

        -label <text> <object>

    ::

            assign the specified label text to the specified object. The object can
            be a single selection wildcard expressions or a saved set of objects in
            the @<name> syntax (see "help select" for details).


    .. code:: yoscrypt

        -colors <seed>

    ::

            Randomly assign colors to the wires. The integer argument is the seed
            for the random number generator. Change the seed value if the colored
            graph still is ambiguous. A seed of zero deactivates the coloring.


    .. code:: yoscrypt

        -colorattr <attribute_name>

    ::

            Use the specified attribute to assign colors. A unique color is
            assigned to each unique value of this attribute.


    .. code:: yoscrypt

        -width

    ::

            annotate buses with a label indicating the width of the bus.


    .. code:: yoscrypt

        -signed

    ::

            mark ports (A, B) that are declared as signed (using the [AB]_SIGNED
            cell parameter) with an asterisk next to the port name.


    .. code:: yoscrypt

        -stretch

    ::

            stretch the graph so all inputs are on the left side and all outputs
            (including inout ports) are on the right side.


    .. code:: yoscrypt

        -pause

    ::

            wait for the user to press enter to before returning


    .. code:: yoscrypt

        -enum

    ::

            enumerate objects with internal ($-prefixed) names


    .. code:: yoscrypt

        -long

    ::

            do not abbreviate objects with internal ($-prefixed) names


    .. code:: yoscrypt

        -notitle

    ::

            do not add the module name as graph title to the dot file


    .. code:: yoscrypt

        -nobg

    ::

            don't run viewer in the background, IE wait for the viewer tool to
            exit before returning


    ::

        When no <format> is specified, 'dot' is used. When no <format> and <viewer> is
        specified, 'xdot' is used to display the schematic (POSIX systems only).

        The generated output files are '~/.yosys_show.dot' and '~/.yosys_show.<format>',
        unless another prefix is specified using -prefix <prefix>.

        Yosys on Windows and YosysJS use different defaults: The output is written
        to 'show.dot' in the current directory and new viewer is launched each time
        the 'show' command is executed.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            show [options] [selection]
        
        Create a graphviz DOT file for the selected part of the design and compile it
        to a graphics file (usually SVG or PostScript).
        
            -viewer <viewer>
                Run the specified command with the graphics file as parameter.
                On Windows, this pauses yosys until the viewer exits.
                Use "-viewer none" to not run any command.
        
            -format <format>
                Generate a graphics file in the specified format. Use 'dot' to just
                generate a .dot file, or other <format> strings such as 'svg' or 'ps'
                to generate files in other formats (this calls the 'dot' command).
        
            -lib <verilog_or_rtlil_file>
                Use the specified library file for determining whether cell ports are
                inputs or outputs. This option can be used multiple times to specify
                more than one library.
        
                note: in most cases it is better to load the library before calling
                show with 'read_verilog -lib <filename>'. it is also possible to
                load liberty files with 'read_liberty -lib <filename>'.
        
            -prefix <prefix>
                generate <prefix>.* instead of ~/.yosys_show.*
        
            -color <color> <object>
                assign the specified color to the specified object. The object can be
                a single selection wildcard expressions or a saved set of objects in
                the @<name> syntax (see "help select" for details).
        
            -label <text> <object>
                assign the specified label text to the specified object. The object can
                be a single selection wildcard expressions or a saved set of objects in
                the @<name> syntax (see "help select" for details).
        
            -colors <seed>
                Randomly assign colors to the wires. The integer argument is the seed
                for the random number generator. Change the seed value if the colored
                graph still is ambiguous. A seed of zero deactivates the coloring.
        
            -colorattr <attribute_name>
                Use the specified attribute to assign colors. A unique color is
                assigned to each unique value of this attribute.
        
            -width
                annotate buses with a label indicating the width of the bus.
        
            -signed
                mark ports (A, B) that are declared as signed (using the [AB]_SIGNED
                cell parameter) with an asterisk next to the port name.
        
            -stretch
                stretch the graph so all inputs are on the left side and all outputs
                (including inout ports) are on the right side.
        
            -pause
                wait for the user to press enter to before returning
        
            -enum
                enumerate objects with internal ($-prefixed) names
        
            -long
                do not abbreviate objects with internal ($-prefixed) names
        
            -notitle
                do not add the module name as graph title to the dot file
        
            -nobg
                don't run viewer in the background, IE wait for the viewer tool to
                exit before returning
        
        When no <format> is specified, 'dot' is used. When no <format> and <viewer> is
        specified, 'xdot' is used to display the schematic (POSIX systems only).
        
        The generated output files are '~/.yosys_show.dot' and '~/.yosys_show.<format>',
        unless another prefix is specified using -prefix <prefix>.
        
        Yosys on Windows and YosysJS use different defaults: The output is written
        to 'show.dot' in the current directory and new viewer is launched each time
        the 'show' command is executed.
        
