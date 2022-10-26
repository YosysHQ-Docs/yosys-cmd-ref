================================
flowmap - pack LUTs with FlowMap
================================

.. only:: html

    :code:`yosys> help flowmap`
    ----------------------------------------------------------------------------


    :code:`flowmap [options] [selection]` ::

        This pass uses the FlowMap technology mapping algorithm to pack logic gates
        into k-LUTs with optimal depth. It allows mapping any circuit elements that can
        be evaluated with the `eval` pass, including cells with multiple output ports
        and multi-bit input and output ports.


    :code:`-maxlut k` ::

            perform technology mapping for a k-LUT architecture. if not specified,
            defaults to 3.


    :code:`-minlut n` ::

            only produce n-input or larger LUTs. if not specified, defaults to 1.


    :code:`-cells <cell>[,<cell>,...]` ::

            map specified cells. if not specified, maps $_NOT_, $_AND_, $_OR_,
            $_XOR_ and $_MUX_, which are the outputs of the `simplemap` pass.


    :code:`-relax` ::

            perform depth relaxation and area minimization.


    :code:`-r-alpha n, -r-beta n, -r-gamma n` ::

            parameters of depth relaxation heuristic potential function.
            if not specified, alpha=8, beta=2, gamma=1.


    :code:`-optarea n` ::

            optimize for area by trading off at most n logic levels for fewer LUTs.
            n may be zero, to optimize for area without increasing depth.
            implies -relax.


    :code:`-debug` ::

            dump intermediate graphs.


    :code:`-debug-relax` ::

            explain decisions performed during depth relaxation.

.. only:: latex

    ::

        
            flowmap [options] [selection]
        
        This pass uses the FlowMap technology mapping algorithm to pack logic gates
        into k-LUTs with optimal depth. It allows mapping any circuit elements that can
        be evaluated with the `eval` pass, including cells with multiple output ports
        and multi-bit input and output ports.
        
            -maxlut k
                perform technology mapping for a k-LUT architecture. if not specified,
                defaults to 3.
        
            -minlut n
                only produce n-input or larger LUTs. if not specified, defaults to 1.
        
            -cells <cell>[,<cell>,...]
                map specified cells. if not specified, maps $_NOT_, $_AND_, $_OR_,
                $_XOR_ and $_MUX_, which are the outputs of the `simplemap` pass.
        
            -relax
                perform depth relaxation and area minimization.
        
            -r-alpha n, -r-beta n, -r-gamma n
                parameters of depth relaxation heuristic potential function.
                if not specified, alpha=8, beta=2, gamma=1.
        
            -optarea n
                optimize for area by trading off at most n logic levels for fewer LUTs.
                n may be zero, to optimize for area without increasing depth.
                implies -relax.
        
            -debug
                dump intermediate graphs.
        
            -debug-relax
                explain decisions performed during depth relaxation.
        
