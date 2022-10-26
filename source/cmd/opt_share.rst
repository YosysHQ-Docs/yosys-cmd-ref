======================================================================================
opt_share - merge mutually exclusive cells of the same type that share an input signal
======================================================================================

.. only:: html

    :code:`yosys> help opt_share`
    ----------------------------------------------------------------------------


    :code:`opt_share [selection]` ::

        This pass identifies mutually exclusive cells of the same type that:
            (a) share an input signal,
            (b) drive the same $mux, $_MUX_, or $pmux multiplexing cell,

        allowing the cell to be merged and the multiplexer to be moved from
        multiplexing its output to multiplexing the non-shared input signals.

.. only:: latex

    ::

        
            opt_share [selection]
        
        This pass identifies mutually exclusive cells of the same type that:
            (a) share an input signal,
            (b) drive the same $mux, $_MUX_, or $pmux multiplexing cell,
        
        allowing the cell to be merged and the multiplexer to be moved from
        multiplexing its output to multiplexing the non-shared input signals.
        
