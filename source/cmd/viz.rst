===============================
viz - visualize data flow graph
===============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help viz`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        viz [options] [selection]

    ::

        Create a graphviz DOT file for the selected part of the design, showing the
        relationships between the selected wires, and compile it to a graphics
        file (usually SVG or PostScript).


    .. code:: yoscrypt

        -viewer <viewer>

    ::

            Run the specified command with the graphics file as parameter.
            On Windows, this pauses yosys until the viewer exits.


    .. code:: yoscrypt

        -format <format>

    ::

            Generate a graphics file in the specified format. Use 'dot' to just
            generate a .dot file, or other <format> strings such as 'svg' or 'ps'
            to generate files in other formats (this calls the 'dot' command).


    .. code:: yoscrypt

        -prefix <prefix>

    ::

            generate <prefix>.* instead of ~/.yosys_viz.*


    .. code:: yoscrypt

        -pause

    ::

            wait for the user to press enter to before returning


    .. code:: yoscrypt

        -nobg

    ::

            don't run viewer in the background, IE wait for the viewer tool to
            exit before returning


    .. code:: yoscrypt

        -set-vg-attr

    ::

            set their group index as 'vg' attribute on cells and wires


    .. code:: yoscrypt

        -g <selection>

    ::

            manually define a group of terminal signals. this group is not being
            merged with other terminal groups.


    .. code:: yoscrypt

        -u <selection>

    ::

            manually define a unique group for each wire in the selection.


    .. code:: yoscrypt

        -x <selection>

    ::

            manually exclude wires from being considered. (usually this is
            used for global signals, such as reset.)


    .. code:: yoscrypt

        -s <selection>

    ::

            like -g, but mark group as 'special', changing the algorithm to
            preserve as much info about this groups connectivity as possible.


    .. code:: yoscrypt

        -G <selection_expr> .

   

    .. code:: yoscrypt

        -U <selection_expr> .

   

    .. code:: yoscrypt

        -X <selection_expr> .

   

    .. code:: yoscrypt

        -S <selection_expr> .

    ::

            like -u, -g, -x, and -s, but parse all arguments up to a terminating .
            as a single select expression. (see 'help select' for details)


    .. code:: yoscrypt

        -0, -1, -2, -3, -4, -5, -6, -7, -8, -9

    ::

            select effort level. each level corresponds to an incresingly more
            aggressive sequence of strategies for merging nodes of the data flow
            graph. (default: 9)


    ::

        When no <format> is specified, 'dot' is used. When no <format> and <viewer> is
        specified, 'xdot' is used to display the schematic (POSIX systems only).

        The generated output files are '~/.yosys_viz.dot' and '~/.yosys_viz.<format>',
        unless another prefix is specified using -prefix <prefix>.

        Yosys on Windows and YosysJS use different defaults: The output is written
        to 'show.dot' in the current directory and new viewer is launched each time
        the 'show' command is executed.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            viz [options] [selection]
        
        Create a graphviz DOT file for the selected part of the design, showing the
        relationships between the selected wires, and compile it to a graphics
        file (usually SVG or PostScript).
        
            -viewer <viewer>
                Run the specified command with the graphics file as parameter.
                On Windows, this pauses yosys until the viewer exits.
        
            -format <format>
                Generate a graphics file in the specified format. Use 'dot' to just
                generate a .dot file, or other <format> strings such as 'svg' or 'ps'
                to generate files in other formats (this calls the 'dot' command).
        
            -prefix <prefix>
                generate <prefix>.* instead of ~/.yosys_viz.*
        
            -pause
                wait for the user to press enter to before returning
        
            -nobg
                don't run viewer in the background, IE wait for the viewer tool to
                exit before returning
        
            -set-vg-attr
                set their group index as 'vg' attribute on cells and wires
        
            -g <selection>
                manually define a group of terminal signals. this group is not being
                merged with other terminal groups.
        
            -u <selection>
                manually define a unique group for each wire in the selection.
        
            -x <selection>
                manually exclude wires from being considered. (usually this is
                used for global signals, such as reset.)
        
            -s <selection>
                like -g, but mark group as 'special', changing the algorithm to
                preserve as much info about this groups connectivity as possible.
        
            -G <selection_expr> .
            -U <selection_expr> .
            -X <selection_expr> .
            -S <selection_expr> .
                like -u, -g, -x, and -s, but parse all arguments up to a terminating .
                as a single select expression. (see 'help select' for details)
        
            -0, -1, -2, -3, -4, -5, -6, -7, -8, -9
                select effort level. each level corresponds to an incresingly more
                aggressive sequence of strategies for merging nodes of the data flow
                graph. (default: 9)
        
        When no <format> is specified, 'dot' is used. When no <format> and <viewer> is
        specified, 'xdot' is used to display the schematic (POSIX systems only).
        
        The generated output files are '~/.yosys_viz.dot' and '~/.yosys_viz.<format>',
        unless another prefix is specified using -prefix <prefix>.
        
        Yosys on Windows and YosysJS use different defaults: The output is written
        to 'show.dot' in the current directory and new viewer is launched each time
        the 'show' command is executed.
        
