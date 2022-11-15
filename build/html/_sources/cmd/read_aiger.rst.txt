============================
read_aiger - read AIGER file
============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help read_aiger`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        read_aiger [options] [filename]

    ::

        Load module from an AIGER file into the current design.


    .. code:: yoscrypt

        -module_name <module_name>

    ::

            name of module to be created (default: <filename>)


    .. code:: yoscrypt

        -clk_name <wire_name>

    ::

            if specified, AIGER latches to be transformed into $_DFF_P_ cells
            clocked by wire of this name. otherwise, $_FF_ cells will be used


    .. code:: yoscrypt

        -map <filename>

    ::

            read file with port and latch symbols


    .. code:: yoscrypt

        -wideports

    ::

            merge ports that match the pattern 'name[int]' into a single
            multi-bit port 'name'


    .. code:: yoscrypt

        -xaiger

    ::

            read XAIGER extensions

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            read_aiger [options] [filename]
        
        Load module from an AIGER file into the current design.
        
            -module_name <module_name>
                name of module to be created (default: <filename>)
        
            -clk_name <wire_name>
                if specified, AIGER latches to be transformed into $_DFF_P_ cells
                clocked by wire of this name. otherwise, $_FF_ cells will be used
        
            -map <filename>
                read file with port and latch symbols
        
            -wideports
                merge ports that match the pattern 'name[int]' into a single
                multi-bit port 'name'
        
            -xaiger
                read XAIGER extensions
        
