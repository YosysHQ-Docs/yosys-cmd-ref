========================
flatten - flatten design
========================

.. raw:: latex

    \begin{comment}

.. cmd:def:: flatten
    :title: flatten design



    .. code:: yoscrypt

        flatten [options] [selection]

    ::

        This pass flattens the design by replacing cells by their implementation. This
        pass is very similar to the 'techmap' pass. The only difference is that this
        pass is using the current design as mapping library.

        Cells and/or modules with the 'keep_hierarchy' attribute set will not be
        flattened by this command.


    .. code:: yoscrypt

        -wb

    ::

            Ignore the 'whitebox' attribute on cell implementations.


    .. code:: yoscrypt

        -noscopeinfo

    ::

            Do not create '$scopeinfo' cells that preserve attributes of cells and
            modules that were removed during flattening. With this option, the
            'src' attribute of a given cell is merged into all objects replacing
            that cell, with multiple distinct 'src' locations separated by '|'.
            Without this option these 'src' locations can be found via the
            cell_src' and 'module_src' attribute of '$scopeinfo' cells.


    .. code:: yoscrypt

        -scopename

    ::

            Create 'scopename' attributes for objects with a private name. This
            attribute records the 'hdlname' of the enclosing scope. For objects
            with a public name the enclosing scope can be found via their
            'hdlname' attribute.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            flatten [options] [selection]
        
        This pass flattens the design by replacing cells by their implementation. This
        pass is very similar to the 'techmap' pass. The only difference is that this
        pass is using the current design as mapping library.
        
        Cells and/or modules with the 'keep_hierarchy' attribute set will not be
        flattened by this command.
        
            -wb
                Ignore the 'whitebox' attribute on cell implementations.
        
            -noscopeinfo
                Do not create '$scopeinfo' cells that preserve attributes of cells and
                modules that were removed during flattening. With this option, the
                'src' attribute of a given cell is merged into all objects replacing
                that cell, with multiple distinct 'src' locations separated by '|'.
                Without this option these 'src' locations can be found via the
                cell_src' and 'module_src' attribute of '$scopeinfo' cells.
        
            -scopename
                Create 'scopename' attributes for objects with a private name. This
                attribute records the 'hdlname' of the enclosing scope. For objects
                with a public name the enclosing scope can be found via their
                'hdlname' attribute.
        
