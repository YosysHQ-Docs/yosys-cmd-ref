====================================
abc9_ops - helper functions for ABC9
====================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: abc9_ops
    :title: helper functions for ABC9



    .. code:: yoscrypt

        abc9_ops [options] [selection]

    ::

        This pass contains a set of supporting operations for use during ABC technology
        mapping, and is expected to be called in conjunction with other operations from
        the `abc9' script pass. Only fully-selected modules are supported.


    .. code:: yoscrypt

        -check

    ::

            check that the design is valid, e.g. (* abc9_box_id *) values are
            unique, (* abc9_carry *) is only given for one input/output port, etc.


    .. code:: yoscrypt

        -prep_hier

    ::

            derive all used (* abc9_box *) or (* abc9_flop *) (if -dff option)
            whitebox modules. with (* abc9_flop *) modules, only those containing
            $dff/$_DFF_[NP]_ cells with zero initial state -- due to an ABC
            limitation -- will be derived.


    .. code:: yoscrypt

        -prep_bypass

    ::

            create techmap rules in the '$abc9_map' and '$abc9_unmap' designs for
            bypassing sequential (* abc9_box *) modules using a combinatorial box
            (named *_$abc9_byp). bypassing is necessary if sequential elements (e.g.
            $dff, $mem, etc.) are discovered inside so that any combinatorial paths
            will be correctly captured. this bypass box will only contain ports that
            are referenced by a simple path declaration ($specify2 cell) inside a
            specify block.


    .. code:: yoscrypt

        -prep_dff

    ::

            select all (* abc9_flop *) modules instantiated in the design and store
            in the named selection '$abc9_flops'.


    .. code:: yoscrypt

        -prep_dff_submod

    ::

            within (* abc9_flop *) modules, rewrite all edge-sensitive path
            declarations and $setup() timing checks ($specify3 and $specrule cells)
            that share a 'DST' port with the $_DFF_[NP]_.Q port from this 'Q' port
            to the DFF's 'D' port. this is to prepare such specify cells to be moved
            into the flop box.


    .. code:: yoscrypt

        -prep_dff_unmap

    ::

            populate the '$abc9_unmap' design with techmap rules for mapping
            *_$abc9_flop cells back into their derived cell types (where the rules
            created by -prep_hier will then map back to the original cell with
            parameters).


    .. code:: yoscrypt

        -prep_delays

    ::

            insert `$__ABC9_DELAY' blackbox cells into the design to account for
            certain required times.


    .. code:: yoscrypt

        -break_scc

    ::

            for an arbitrarily chosen cell in each unique SCC of each selected
            module (tagged with an (* abc9_scc_id = <int> *) attribute) interrupt
            all wires driven by this cell's outputs with a temporary
            $__ABC9_SCC_BREAKER cell to break the SCC.


    .. code:: yoscrypt

        -prep_xaiger

    ::

            prepare the design for XAIGER output. this includes computing the
            topological ordering of ABC9 boxes, as well as preparing the 
            '$abc9_holes' design that contains the logic behaviour of ABC9
            whiteboxes.


    .. code:: yoscrypt

        -dff

    ::

            consider flop cells (those instantiating modules marked with
            (* abc9_flop *)) during -prep_{delays,xaiger,box}.


    .. code:: yoscrypt

        -prep_lut <maxlut>

    ::

            pre-compute the lut library by analysing all modules marked with
            (* abc9_lut=<area> *).


    .. code:: yoscrypt

        -write_lut <dst>

    ::

            write the pre-computed lut library to <dst>.


    .. code:: yoscrypt

        -prep_box

    ::

            pre-compute the box library by analysing all modules marked with
            (* abc9_box *).


    .. code:: yoscrypt

        -write_box <dst>

    ::

            write the pre-computed box library to <dst>.


    .. code:: yoscrypt

        -reintegrate

    ::

            for each selected module, re-intergrate the module '<module-name>$abc9'
            by first recovering ABC9 boxes, and then stitching in the remaining
            primary inputs and outputs.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            abc9_ops [options] [selection]
        
        This pass contains a set of supporting operations for use during ABC technology
        mapping, and is expected to be called in conjunction with other operations from
        the `abc9' script pass. Only fully-selected modules are supported.
        
            -check
                check that the design is valid, e.g. (* abc9_box_id *) values are
                unique, (* abc9_carry *) is only given for one input/output port, etc.
        
            -prep_hier
                derive all used (* abc9_box *) or (* abc9_flop *) (if -dff option)
                whitebox modules. with (* abc9_flop *) modules, only those containing
                $dff/$_DFF_[NP]_ cells with zero initial state -- due to an ABC
                limitation -- will be derived.
        
            -prep_bypass
                create techmap rules in the '$abc9_map' and '$abc9_unmap' designs for
                bypassing sequential (* abc9_box *) modules using a combinatorial box
                (named *_$abc9_byp). bypassing is necessary if sequential elements (e.g.
                $dff, $mem, etc.) are discovered inside so that any combinatorial paths
                will be correctly captured. this bypass box will only contain ports that
                are referenced by a simple path declaration ($specify2 cell) inside a
                specify block.
        
            -prep_dff
                select all (* abc9_flop *) modules instantiated in the design and store
                in the named selection '$abc9_flops'.
        
            -prep_dff_submod
                within (* abc9_flop *) modules, rewrite all edge-sensitive path
                declarations and $setup() timing checks ($specify3 and $specrule cells)
                that share a 'DST' port with the $_DFF_[NP]_.Q port from this 'Q' port
                to the DFF's 'D' port. this is to prepare such specify cells to be moved
                into the flop box.
        
            -prep_dff_unmap
                populate the '$abc9_unmap' design with techmap rules for mapping
                *_$abc9_flop cells back into their derived cell types (where the rules
                created by -prep_hier will then map back to the original cell with
                parameters).
        
            -prep_delays
                insert `$__ABC9_DELAY' blackbox cells into the design to account for
                certain required times.
        
            -break_scc
                for an arbitrarily chosen cell in each unique SCC of each selected
                module (tagged with an (* abc9_scc_id = <int> *) attribute) interrupt
                all wires driven by this cell's outputs with a temporary
                $__ABC9_SCC_BREAKER cell to break the SCC.
        
            -prep_xaiger
                prepare the design for XAIGER output. this includes computing the
                topological ordering of ABC9 boxes, as well as preparing the 
                '$abc9_holes' design that contains the logic behaviour of ABC9
                whiteboxes.
        
            -dff
                consider flop cells (those instantiating modules marked with
                (* abc9_flop *)) during -prep_{delays,xaiger,box}.
        
            -prep_lut <maxlut>
                pre-compute the lut library by analysing all modules marked with
                (* abc9_lut=<area> *).
        
            -write_lut <dst>
                write the pre-computed lut library to <dst>.
        
            -prep_box
                pre-compute the box library by analysing all modules marked with
                (* abc9_box *).
        
            -write_box <dst>
                write the pre-computed box library to <dst>.
        
            -reintegrate
                for each selected module, re-intergrate the module '<module-name>$abc9'
                by first recovering ABC9 boxes, and then stitching in the remaining
                primary inputs and outputs.
        
