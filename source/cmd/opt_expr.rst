================================================================
opt_expr - perform const folding and simple expression rewriting
================================================================

.. only:: html

    :code:`yosys> help opt_expr`
    ----------------------------------------------------------------------------


    :code:`opt_expr [options] [selection]` ::

        This pass performs const folding on internal cell types with constant inputs.
        It also performs some simple expression rewriting.


    :code:`-mux_undef` ::

            remove 'undef' inputs from $mux, $pmux and $_MUX_ cells


    :code:`-mux_bool` ::

            replace $mux cells with inverters or buffers when possible


    :code:`-undriven` ::

            replace undriven nets with undef (x) constants


    :code:`-noclkinv` ::

            do not optimize clock inverters by changing FF types


    :code:`-fine` ::

            perform fine-grain optimizations


    :code:`-full` ::

            alias for -mux_undef -mux_bool -undriven -fine


    :code:`-keepdc` ::

            some optimizations change the behavior of the circuit with respect to
            don't-care bits. for example in 'a+0' a single x-bit in 'a' will cause
            all result bits to be set to x. this behavior changes when 'a+0' is
            replaced by 'a'. the -keepdc option disables all such optimizations.

.. only:: latex

    ::

        
            opt_expr [options] [selection]
        
        This pass performs const folding on internal cell types with constant inputs.
        It also performs some simple expression rewriting.
        
            -mux_undef
                remove 'undef' inputs from $mux, $pmux and $_MUX_ cells
        
            -mux_bool
                replace $mux cells with inverters or buffers when possible
        
            -undriven
                replace undriven nets with undef (x) constants
        
            -noclkinv
                do not optimize clock inverters by changing FF types
        
            -fine
                perform fine-grain optimizations
        
            -full
                alias for -mux_undef -mux_bool -undriven -fine
        
            -keepdc
                some optimizations change the behavior of the circuit with respect to
                don't-care bits. for example in 'a+0' a single x-bit in 'a' will cause
                all result bits to be set to x. this behavior changes when 'a+0' is
                replaced by 'a'. the -keepdc option disables all such optimizations.
        
