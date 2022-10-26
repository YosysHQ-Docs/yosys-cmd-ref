===============================================
cutpoint - adds formal cut points to the design
===============================================

.. only:: html

    :code:`yosys> help cutpoint`
    ----------------------------------------------------------------------------


    :code:`cutpoint [options] [selection]` ::

        This command adds formal cut points to the design.


    :code:`-undef` ::

            set cupoint nets to undef (x). the default behavior is to create a
            $anyseq cell and drive the cutpoint net from that

.. only:: latex

    ::

        
            cutpoint [options] [selection]
        
        This command adds formal cut points to the design.
        
            -undef
                set cupoint nets to undef (x). the default behavior is to create a
                $anyseq cell and drive the cutpoint net from that
        
