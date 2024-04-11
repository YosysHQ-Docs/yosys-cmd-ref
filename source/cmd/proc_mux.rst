=================================================
proc_mux - convert decision trees to multiplexers
=================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: proc_mux
    :title: convert decision trees to multiplexers



    .. code:: yoscrypt

        proc_mux [options] [selection]

    ::

        This pass converts the decision trees in processes (originating from if-else
        and case statements) to trees of multiplexer cells.


    .. code:: yoscrypt

        -ifx

    ::

            Use Verilog simulation behavior with respect to undef values in
            'case' expressions and 'if' conditions.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            proc_mux [options] [selection]
        
        This pass converts the decision trees in processes (originating from if-else
        and case statements) to trees of multiplexer cells.
        
            -ifx
                Use Verilog simulation behavior with respect to undef values in
                'case' expressions and 'if' conditions.
        
