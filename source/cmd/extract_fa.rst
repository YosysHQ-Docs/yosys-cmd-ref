==============================================
extract_fa - find and extract full/half adders
==============================================

.. only:: html

    :code:`yosys> help extract_fa`
    ----------------------------------------------------------------------------


    :code:`extract_fa [options] [selection]` ::

        This pass extracts full/half adders from a gate-level design.


    :code:`-fa, -ha` ::

            Enable cell types (fa=full adder, ha=half adder)
            All types are enabled if none of this options is used


    :code:`-d <int>` ::

            Set maximum depth for extracted logic cones (default=20)


    :code:`-b <int>` ::

            Set maximum breadth for extracted logic cones (default=6)


    :code:`-v` ::

            Verbose output

.. only:: latex

    ::

        
            extract_fa [options] [selection]
        
        This pass extracts full/half adders from a gate-level design.
        
            -fa, -ha
                Enable cell types (fa=full adder, ha=half adder)
                All types are enabled if none of this options is used
        
            -d <int>
                Set maximum depth for extracted logic cones (default=20)
        
            -b <int>
                Set maximum breadth for extracted logic cones (default=6)
        
            -v
                Verbose output
        
