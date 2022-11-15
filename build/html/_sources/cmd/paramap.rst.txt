==================================
paramap - renaming cell parameters
==================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help paramap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        paramap [options] [selection]

    ::

        This command renames cell parameters and/or maps key/value pairs to
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


    ::

        For example, mapping Diamond-style ECP5 "init" attributes to Yosys-style:

            paramap -tocase INIT t:LUT4

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            paramap [options] [selection]
        
        This command renames cell parameters and/or maps key/value pairs to
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
        
        For example, mapping Diamond-style ECP5 "init" attributes to Yosys-style:
        
            paramap -tocase INIT t:LUT4
        
