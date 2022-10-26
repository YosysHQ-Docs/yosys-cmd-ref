===============================================
ice40_opt - iCE40: perform simple optimizations
===============================================

.. only:: html

    :code:`yosys> help ice40_opt`
    ----------------------------------------------------------------------------


    :code:`ice40_opt [options] [selection]` ::

        This command executes the following script:

            do
                <ice40 specific optimizations>
                opt_expr -mux_undef -undriven [-full]
                opt_merge
                opt_dff
                opt_clean
            while <changed design>

.. only:: latex

    ::

        
            ice40_opt [options] [selection]
        
        This command executes the following script:
        
            do
                <ice40 specific optimizations>
                opt_expr -mux_undef -undriven [-full]
                opt_merge
                opt_dff
                opt_clean
            while <changed design>
        
