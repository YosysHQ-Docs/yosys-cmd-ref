========================================================
cellmatch - match cells to their targets in cell library
========================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: cellmatch
    :title: match cells to their targets in cell library



    .. code:: yoscrypt

        cellmatch -lib <design> [module selection]

    ::

        This pass identifies functionally equivalent counterparts between each of the
        selected modules and a module from the secondary design <design>. For every such
        correspondence found, a techmap rule is generated for mapping instances of the
        former to instances of the latter. This techmap rule is saved in yet another
        design called '$cellmatch', which is created if non-existent.

        This pass restricts itself to combinational modules. Modules are functionally
        equivalent as long as their truth tables are identical upto a permutation of
        inputs and outputs. The supported number of inputs is limited to 6.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            cellmatch -lib <design> [module selection]
        
        This pass identifies functionally equivalent counterparts between each of the
        selected modules and a module from the secondary design <design>. For every such
        correspondence found, a techmap rule is generated for mapping instances of the
        former to instances of the latter. This techmap rule is saved in yet another
        design called '$cellmatch', which is created if non-existent.
        
        This pass restricts itself to combinational modules. Modules are functionally
        equivalent as long as their truth tables are identical upto a permutation of
        inputs and outputs. The supported number of inputs is limited to 6.
        
