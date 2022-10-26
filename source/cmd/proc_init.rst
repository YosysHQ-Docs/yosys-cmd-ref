====================================================
proc_init - convert initial block to init attributes
====================================================

.. only:: html

    :code:`yosys> help proc_init`
    ----------------------------------------------------------------------------


    :code:`proc_init [selection]` ::

        This pass extracts the 'init' actions from processes (generated from Verilog
        'initial' blocks) and sets the initial value to the 'init' attribute on the
        respective wire.

.. only:: latex

    ::

        
            proc_init [selection]
        
        This pass extracts the 'init' actions from processes (generated from Verilog
        'initial' blocks) and sets the initial value to the 'init' attribute on the
        respective wire.
        
