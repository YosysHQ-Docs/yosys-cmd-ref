===============================================
cutpoint - adds formal cut points to the design
===============================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: cutpoint
    :title: adds formal cut points to the design



    .. code:: yoscrypt

        cutpoint [options] [selection]

    ::

        This command adds formal cut points to the design.


    .. code:: yoscrypt

        -undef

    ::

            set cupoint nets to undef (x). the default behavior is to create a
            $anyseq cell and drive the cutpoint net from that

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            cutpoint [options] [selection]
        
        This command adds formal cut points to the design.
        
            -undef
                set cupoint nets to undef (x). the default behavior is to create a
                $anyseq cell and drive the cutpoint net from that
        
