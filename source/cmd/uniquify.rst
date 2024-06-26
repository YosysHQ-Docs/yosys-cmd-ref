==========================================
uniquify - create unique copies of modules
==========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: uniquify
    :title: create unique copies of modules



    .. code:: yoscrypt

        uniquify [selection]

    ::

        By default, a module that is instantiated by several other modules is only
        kept once in the design. This preserves the original modularity of the design
        and reduces the overall size of the design in memory. But it prevents certain
        optimizations and other operations on the design. This pass creates unique
        modules for all selected cells. The created modules are marked with the
        'unique' attribute.

        This commands only operates on modules that by themself have the 'unique'
        attribute set (the 'top' module is unique implicitly).

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            uniquify [selection]
        
        By default, a module that is instantiated by several other modules is only
        kept once in the design. This preserves the original modularity of the design
        and reduces the overall size of the design in memory. But it prevents certain
        optimizations and other operations on the design. This pass creates unique
        modules for all selected cells. The created modules are marked with the
        'unique' attribute.
        
        This commands only operates on modules that by themself have the 'unique'
        attribute set (the 'top' module is unique implicitly).
        
