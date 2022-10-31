=========================================
opt_clean - remove unused cells and wires
=========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help opt_clean`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        opt_clean [options] [selection]

    ::

        This pass identifies wires and cells that are unused and removes them. Other
        passes often remove cells but leave the wires in the design or reconnect the
        wires but leave the old cells in the design. This pass can be used to clean up
        after the passes that do the actual work.

        This pass only operates on completely selected modules without processes.


    .. code:: yoscrypt

        -purge

    ::

            also remove internal nets if they have a public name

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            opt_clean [options] [selection]
        
        This pass identifies wires and cells that are unused and removes them. Other
        passes often remove cells but leave the wires in the design or reconnect the
        wires but leave the old cells in the design. This pass can be used to clean up
        after the passes that do the actual work.
        
        This pass only operates on completely selected modules without processes.
        
            -purge
                also remove internal nets if they have a public name
        
