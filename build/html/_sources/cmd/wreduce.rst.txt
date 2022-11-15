========================================================
wreduce - reduce the word size of operations if possible
========================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help wreduce`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        wreduce [options] [selection]

    ::

        This command reduces the word size of operations. For example it will replace
        the 32 bit adders in the following code with adders of more appropriate widths:

            module test(input [3:0] a, b, c, output [7:0] y);
                assign y = a + b + c + 1;
            endmodule

        Options:


    .. code:: yoscrypt

        -memx

    ::

            Do not change the width of memory address ports. Use this options in
            flows that use the 'memory_memx' pass.


    .. code:: yoscrypt

        -mux_undef

    ::

            remove 'undef' inputs from $mux, $pmux and $_MUX_ cells


    .. code:: yoscrypt

        -keepdc

    ::

            Do not optimize explicit don't-care values.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            wreduce [options] [selection]
        
        This command reduces the word size of operations. For example it will replace
        the 32 bit adders in the following code with adders of more appropriate widths:
        
            module test(input [3:0] a, b, c, output [7:0] y);
                assign y = a + b + c + 1;
            endmodule
        
        Options:
        
            -memx
                Do not change the width of memory address ports. Use this options in
                flows that use the 'memory_memx' pass.
        
            -mux_undef
                remove 'undef' inputs from $mux, $pmux and $_MUX_ cells
        
            -keepdc
                Do not optimize explicit don't-care values.
        
