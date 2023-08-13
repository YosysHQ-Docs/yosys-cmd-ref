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
        
