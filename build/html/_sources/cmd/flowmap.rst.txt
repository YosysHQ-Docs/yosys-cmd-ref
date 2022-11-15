================================
flowmap - pack LUTs with FlowMap
================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help flowmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        flowmap [options] [selection]

    ::

        This pass uses the FlowMap technology mapping algorithm to pack logic gates
        into k-LUTs with optimal depth. It allows mapping any circuit elements that can
        be evaluated with the `eval` pass, including cells with multiple output ports
        and multi-bit input and output ports.


    .. code:: yoscrypt

        -maxlut k

    ::

            perform technology mapping for a k-LUT architecture. if not specified,
            defaults to 3.


    .. code:: yoscrypt

        -minlut n

    ::

            only produce n-input or larger LUTs. if not specified, defaults to 1.


    .. code:: yoscrypt

        -cells <cell>[,<cell>,...]

    ::

            map specified cells. if not specified, maps $_NOT_, $_AND_, $_OR_,
            $_XOR_ and $_MUX_, which are the outputs of the `simplemap` pass.


    .. code:: yoscrypt

        -relax

    ::

            perform depth relaxation and area minimization.


    .. code:: yoscrypt

        -r-alpha n, -r-beta n, -r-gamma n

    ::

            parameters of depth relaxation heuristic potential function.
            if not specified, alpha=8, beta=2, gamma=1.


    .. code:: yoscrypt

        -optarea n

    ::

            optimize for area by trading off at most n logic levels for fewer LUTs.
            n may be zero, to optimize for area without increasing depth.
            implies -relax.


    .. code:: yoscrypt

        -debug

    ::

            dump intermediate graphs.


    .. code:: yoscrypt

        -debug-relax

    ::

            explain decisions performed during depth relaxation.

.. raw:: latex

    \end{comment}

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
        
