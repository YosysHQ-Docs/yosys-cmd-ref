==================================
opt - perform simple optimizations
==================================

.. only:: html

    :code:`yosys> help opt`
    ----------------------------------------------------------------------------


    :code:`opt [options] [selection]` ::

        This pass calls all the other opt_* passes in a useful order. This performs
        a series of trivial optimizations and cleanups. This pass executes the other
        passes in the following order:

            opt_expr [-mux_undef] [-mux_bool] [-undriven] [-noclkinv] [-fine] [-full] [-keepdc]
            opt_merge [-share_all] -nomux

            do
                opt_muxtree
                opt_reduce [-fine] [-full]
                opt_merge [-share_all]
                opt_share  (-full only)
                opt_dff [-nodffe] [-nosdff] [-keepdc] [-sat]  (except when called with -noff)
                opt_clean [-purge]
                opt_expr [-mux_undef] [-mux_bool] [-undriven] [-noclkinv] [-fine] [-full] [-keepdc]
            while <changed design>

        When called with -fast the following script is used instead:

            do
                opt_expr [-mux_undef] [-mux_bool] [-undriven] [-noclkinv] [-fine] [-full] [-keepdc]
                opt_merge [-share_all]
                opt_dff [-nodffe] [-nosdff] [-keepdc] [-sat]  (except when called with -noff)
                opt_clean [-purge]
            while <changed design in opt_dff>

        Note: Options in square brackets (such as [-keepdc]) are passed through to
        the opt_* commands when given to 'opt'.


.. only:: latex

    ::

        
            opt [options] [selection]
        
        This pass calls all the other opt_* passes in a useful order. This performs
        a series of trivial optimizations and cleanups. This pass executes the other
        passes in the following order:
        
            opt_expr [-mux_undef] [-mux_bool] [-undriven] [-noclkinv] [-fine] [-full] [-keepdc]
            opt_merge [-share_all] -nomux
        
            do
                opt_muxtree
                opt_reduce [-fine] [-full]
                opt_merge [-share_all]
                opt_share  (-full only)
                opt_dff [-nodffe] [-nosdff] [-keepdc] [-sat]  (except when called with -noff)
                opt_clean [-purge]
                opt_expr [-mux_undef] [-mux_bool] [-undriven] [-noclkinv] [-fine] [-full] [-keepdc]
            while <changed design>
        
        When called with -fast the following script is used instead:
        
            do
                opt_expr [-mux_undef] [-mux_bool] [-undriven] [-noclkinv] [-fine] [-full] [-keepdc]
                opt_merge [-share_all]
                opt_dff [-nodffe] [-nosdff] [-keepdc] [-sat]  (except when called with -noff)
                opt_clean [-purge]
            while <changed design in opt_dff>
        
        Note: Options in square brackets (such as [-keepdc]) are passed through to
        the opt_* commands when given to 'opt'.
        
        
