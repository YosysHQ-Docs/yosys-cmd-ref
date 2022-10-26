===================================
opt_dff - perform DFF optimizations
===================================

.. only:: html

    :code:`yosys> help opt_dff`
    ----------------------------------------------------------------------------


    :code:`opt_dff [-nodffe] [-nosdff] [-keepdc] [-sat] [selection]` ::

        This pass converts flip-flops to a more suitable type by merging clock enables
        and synchronous reset multiplexers, removing unused control inputs, or
        potentially removes the flip-flop altogether, converting it to a constant
        driver.


    :code:`-nodffe` ::

            disables dff -> dffe conversion, and other transforms recognizing clock
            enable


    :code:`-nosdff` ::

            disables dff -> sdff conversion, and other transforms recognizing sync
            resets


    :code:`-simple-dffe` ::

            only enables clock enable recognition transform for obvious cases


    :code:`-sat` ::

            additionally invoke SAT solver to detect and remove flip-flops (with
            non-constant inputs) that can also be replaced with a constant driver


    :code:`-keepdc` ::

            some optimizations change the behavior of the circuit with respect to
            don't-care bits. for example in 'a+0' a single x-bit in 'a' will cause
            all result bits to be set to x. this behavior changes when 'a+0' is
            replaced by 'a'. the -keepdc option disables all such optimizations.

.. only:: latex

    ::

        
            opt_dff [-nodffe] [-nosdff] [-keepdc] [-sat] [selection]
        
        This pass converts flip-flops to a more suitable type by merging clock enables
        and synchronous reset multiplexers, removing unused control inputs, or
        potentially removes the flip-flop altogether, converting it to a constant
        driver.
        
            -nodffe
                disables dff -> dffe conversion, and other transforms recognizing clock
                enable
        
            -nosdff
                disables dff -> sdff conversion, and other transforms recognizing sync
                resets
        
            -simple-dffe
                only enables clock enable recognition transform for obvious cases
        
            -sat
                additionally invoke SAT solver to detect and remove flip-flops (with
                non-constant inputs) that can also be replaced with a constant driver
        
            -keepdc
                some optimizations change the behavior of the circuit with respect to
                don't-care bits. for example in 'a+0' a single x-bit in 'a' will cause
                all result bits to be set to x. this behavior changes when 'a+0' is
                replaced by 'a'. the -keepdc option disables all such optimizations.
        
