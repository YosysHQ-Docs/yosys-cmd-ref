======================================
proc_arst - detect asynchronous resets
======================================

.. only:: html

    :code:`yosys> help proc_arst`
    ----------------------------------------------------------------------------


    :code:`proc_arst [-global_arst [!]<netname>] [selection]` ::

        This pass identifies asynchronous resets in the processes and converts them
        to a different internal representation that is suitable for generating
        flip-flop cells with asynchronous resets.


    :code:`-global_arst [!]<netname>` ::

            In modules that have a net with the given name, use this net as async
            reset for registers that have been assign initial values in their
            declaration ('reg foobar = constant_value;'). Use the '!' modifier for
            active low reset signals. Note: the frontend stores the default value
            in the 'init' attribute on the net.

.. only:: latex

    ::

        
            proc_arst [-global_arst [!]<netname>] [selection]
        
        This pass identifies asynchronous resets in the processes and converts them
        to a different internal representation that is suitable for generating
        flip-flop cells with asynchronous resets.
        
            -global_arst [!]<netname>
                In modules that have a net with the given name, use this net as async
                reset for registers that have been assign initial values in their
                declaration ('reg foobar = constant_value;'). Use the '!' modifier for
                active low reset signals. Note: the frontend stores the default value
                in the 'init' attribute on the net.
        
