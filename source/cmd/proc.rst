======================================
proc - translate processes to netlists
======================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: proc
    :title: translate processes to netlists



    .. code:: yoscrypt

        proc [options] [selection]

    ::

        This pass calls all the other proc_* passes in the most common order.

            proc_clean
            proc_rmdead
            proc_prune
            proc_init
            proc_arst
            proc_rom
            proc_mux
            proc_dlatch
            proc_dff
            proc_memwr
            proc_clean
            opt_expr -keepdc

        This replaces the processes in the design with multiplexers,
        flip-flops and latches.

        The following options are supported:


    .. code:: yoscrypt

        -nomux

    ::

            Will omit the proc_mux pass.


    .. code:: yoscrypt

        -norom

    ::

            Will omit the proc_rom pass.


    .. code:: yoscrypt

        -global_arst [!]<netname>

    ::

            This option is passed through to proc_arst.


    .. code:: yoscrypt

        -ifx

    ::

            This option is passed through to proc_mux. proc_rmdead is not
            executed in -ifx mode.


    .. code:: yoscrypt

        -noopt

    ::

            Will omit the opt_expr pass.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            proc [options] [selection]
        
        This pass calls all the other proc_* passes in the most common order.
        
            proc_clean
            proc_rmdead
            proc_prune
            proc_init
            proc_arst
            proc_rom
            proc_mux
            proc_dlatch
            proc_dff
            proc_memwr
            proc_clean
            opt_expr -keepdc
        
        This replaces the processes in the design with multiplexers,
        flip-flops and latches.
        
        The following options are supported:
        
            -nomux
                Will omit the proc_mux pass.
        
            -norom
                Will omit the proc_rom pass.
        
            -global_arst [!]<netname>
                This option is passed through to proc_arst.
        
            -ifx
                This option is passed through to proc_mux. proc_rmdead is not
                executed in -ifx mode.
        
            -noopt
                Will omit the opt_expr pass.
        
