===============================
add - add objects to the design
===============================

.. raw:: latex

    \begin{comment}

.. cmd:def:: add
    :title: add objects to the design



    .. code:: yoscrypt

        add <command> [selection]

    ::

        This command adds objects to the design. It operates on all fully selected
        modules. So e.g. 'add -wire foo' will add a wire foo to all selected modules.


    .. code:: yoscrypt

        add {-wire|-input|-inout|-output} <name> <width> [selection]

    ::

        Add a wire (input, inout, output port) with the given name and width. The
        command will fail if the object exists already and has different properties
        than the object to be created.


    .. code:: yoscrypt

        add -global_input <name> <width> [selection]

    ::

        Like 'add -input', but also connect the signal between instances of the
        selected modules.


    .. code:: yoscrypt

        add {-assert|-assume|-live|-fair|-cover} <name1> [-if <name2>]

    ::

        Add an $assert, $assume, etc. cell connected to a wire named name1, with its
        enable signal optionally connected to a wire named name2 (default: 1'b1).


    .. code:: yoscrypt

        add -mod <name[s]>

    ::

        Add module[s] with the specified name[s].

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            add <command> [selection]
        
        This command adds objects to the design. It operates on all fully selected
        modules. So e.g. 'add -wire foo' will add a wire foo to all selected modules.
        
        
            add {-wire|-input|-inout|-output} <name> <width> [selection]
        
        Add a wire (input, inout, output port) with the given name and width. The
        command will fail if the object exists already and has different properties
        than the object to be created.
        
        
            add -global_input <name> <width> [selection]
        
        Like 'add -input', but also connect the signal between instances of the
        selected modules.
        
        
            add {-assert|-assume|-live|-fair|-cover} <name1> [-if <name2>]
        
        Add an $assert, $assume, etc. cell connected to a wire named name1, with its
        enable signal optionally connected to a wire named name2 (default: 1'b1).
        
        
            add -mod <name[s]>
        
        Add module[s] with the specified name[s].
        
