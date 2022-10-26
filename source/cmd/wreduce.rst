========================================================
wreduce - reduce the word size of operations if possible
========================================================

.. only:: html

    :code:`yosys> help wreduce`
    ----------------------------------------------------------------------------


    :code:`wreduce [options] [selection]` ::

        This command reduces the word size of operations. For example it will replace
        the 32 bit adders in the following code with adders of more appropriate widths:

            module test(input [3:0] a, b, c, output [7:0] y);
                assign y = a + b + c + 1;
            endmodule

        Options:


    :code:`-memx` ::

            Do not change the width of memory address ports. Use this options in
            flows that use the 'memory_memx' pass.


    :code:`-mux_undef` ::

            remove 'undef' inputs from $mux, $pmux and $_MUX_ cells


    :code:`-keepdc` ::

            Do not optimize explicit don't-care values.

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
        
