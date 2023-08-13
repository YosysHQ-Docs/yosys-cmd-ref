====================================================
proc_init - convert initial block to init attributes
====================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: proc_init
    :title: convert initial block to init attributes



    .. code:: yoscrypt

        proc_init [selection]

    ::

        This pass extracts the 'init' actions from processes (generated from Verilog
        'initial' blocks) and sets the initial value to the 'init' attribute on the
        respective wire.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            proc_init [selection]
        
        This pass extracts the 'init' actions from processes (generated from Verilog
        'initial' blocks) and sets the initial value to the 'init' attribute on the
        respective wire.
        
