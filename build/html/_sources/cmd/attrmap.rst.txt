=============================
attrmap - renaming attributes
=============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help attrmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        attrmap [options] [selection]

    ::

        This command renames attributes and/or maps key/value pairs to
        other key/value pairs.


    .. code:: yoscrypt

        -tocase <name>

    ::

            Match attribute names case-insensitively and set it to the specified
            name.


    .. code:: yoscrypt

        -rename <old_name> <new_name>

    ::

            Rename attributes as specified


    .. code:: yoscrypt

        -map <old_name>=<old_value> <new_name>=<new_value>

    ::

            Map key/value pairs as indicated.


    .. code:: yoscrypt

        -imap <old_name>=<old_value> <new_name>=<new_value>

    ::

            Like -map, but use case-insensitive match for <old_value> when
            it is a string value.


    .. code:: yoscrypt

        -remove <name>=<value>

    ::

            Remove attributes matching this pattern.


    .. code:: yoscrypt

        -modattr

    ::

            Operate on module attributes instead of attributes on wires and cells.


    ::

        For example, mapping Xilinx-style "keep" attributes to Yosys-style:

            attrmap -tocase keep -imap keep="true" keep=1 \
                    -imap keep="false" keep=0 -remove keep=0

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            attrmap [options] [selection]
        
        This command renames attributes and/or maps key/value pairs to
        other key/value pairs.
        
            -tocase <name>
                Match attribute names case-insensitively and set it to the specified
                name.
        
            -rename <old_name> <new_name>
                Rename attributes as specified
        
            -map <old_name>=<old_value> <new_name>=<new_value>
                Map key/value pairs as indicated.
        
            -imap <old_name>=<old_value> <new_name>=<new_value>
                Like -map, but use case-insensitive match for <old_value> when
                it is a string value.
        
            -remove <name>=<value>
                Remove attributes matching this pattern.
        
            -modattr
                Operate on module attributes instead of attributes on wires and cells.
        
        For example, mapping Xilinx-style "keep" attributes to Yosys-style:
        
            attrmap -tocase keep -imap keep="true" keep=1 \
                    -imap keep="false" keep=0 -remove keep=0
        
