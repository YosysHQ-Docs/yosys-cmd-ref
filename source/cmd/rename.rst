====================================
rename - rename object in the design
====================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: rename
    :title: rename object in the design



    .. code:: yoscrypt

        rename old_name new_name

    ::

        Rename the specified object. Note that selection patterns are not supported
        by this command.



    .. code:: yoscrypt

        rename -output old_name new_name

    ::

        Like above, but also make the wire an output. This will fail if the object is
        not a wire.


    .. code:: yoscrypt

        rename -src [selection]

    ::

        Assign names auto-generated from the src attribute to all selected wires and
        cells with private names.


    .. code:: yoscrypt

        rename -wire [selection] [-suffix <suffix>]

    ::

        Assign auto-generated names based on the wires they drive to all selected
        cells with private names. Ignores cells driving privatly named wires.
        By default, the cell is named after the wire with the cell type as suffix.
        The -suffix option can be used to set the suffix to the given string instead.


    .. code:: yoscrypt

        rename -enumerate [-pattern <pattern>] [selection]

    ::

        Assign short auto-generated names to all selected wires and cells with private
        names. The -pattern option can be used to set the pattern for the new names.
        The character % in the pattern is replaced with a integer number. The default
        pattern is '_%_'.


    .. code:: yoscrypt

        rename -witness

    ::

        Assigns auto-generated names to all $any*/$all* output wires and containing
        cells that do not have a public name. This ensures that, during formal
        verification, a solver-found trace can be fully specified using a public
        hierarchical names.


    .. code:: yoscrypt

        rename -hide [selection]

    ::

        Assign private names (the ones with $-prefix) to all selected wires and cells
        with public names. This ignores all selected ports.


    .. code:: yoscrypt

        rename -top new_name

    ::

        Rename top module.


    .. code:: yoscrypt

        rename -scramble-name [-seed <seed>] [selection]

    ::

        Assign randomly-generated names to all selected wires and cells. The seed option
        can be used to change the random number generator seed from the default, but it
        must be non-zero.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            rename old_name new_name
        
        Rename the specified object. Note that selection patterns are not supported
        by this command.
        
        
        
            rename -output old_name new_name
        
        Like above, but also make the wire an output. This will fail if the object is
        not a wire.
        
        
            rename -src [selection]
        
        Assign names auto-generated from the src attribute to all selected wires and
        cells with private names.
        
        
            rename -wire [selection] [-suffix <suffix>]
        
        Assign auto-generated names based on the wires they drive to all selected
        cells with private names. Ignores cells driving privatly named wires.
        By default, the cell is named after the wire with the cell type as suffix.
        The -suffix option can be used to set the suffix to the given string instead.
        
        
            rename -enumerate [-pattern <pattern>] [selection]
        
        Assign short auto-generated names to all selected wires and cells with private
        names. The -pattern option can be used to set the pattern for the new names.
        The character % in the pattern is replaced with a integer number. The default
        pattern is '_%_'.
        
        
            rename -witness
        
        Assigns auto-generated names to all $any*/$all* output wires and containing
        cells that do not have a public name. This ensures that, during formal
        verification, a solver-found trace can be fully specified using a public
        hierarchical names.
        
        
            rename -hide [selection]
        
        Assign private names (the ones with $-prefix) to all selected wires and cells
        with public names. This ignores all selected ports.
        
        
            rename -top new_name
        
        Rename top module.
        
        
            rename -scramble-name [-seed <seed>] [selection]
        
        Assign randomly-generated names to all selected wires and cells. The seed option
        can be used to change the random number generator seed from the default, but it
        must be non-zero.
        
