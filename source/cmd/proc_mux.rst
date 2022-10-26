=================================================
proc_mux - convert decision trees to multiplexers
=================================================

.. only:: html

    :code:`yosys> help proc_mux`
    ----------------------------------------------------------------------------


    :code:`proc_mux [options] [selection]` ::

        This pass converts the decision trees in processes (originating from if-else
        and case statements) to trees of multiplexer cells.


    :code:`-ifx` ::

            Use Verilog simulation behavior with respect to undef values in
            'case' expressions and 'if' conditions.

.. only:: latex

    ::

        
            proc_mux [options] [selection]
        
        This pass converts the decision trees in processes (originating from if-else
        and case statements) to trees of multiplexer cells.
        
            -ifx
                Use Verilog simulation behavior with respect to undef values in
                'case' expressions and 'if' conditions.
        
