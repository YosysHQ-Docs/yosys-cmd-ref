=============================================
fminit - set init values/sequences for formal
=============================================

.. only:: html

    :code:`yosys> help fminit`
    ----------------------------------------------------------------------------


    :code:`fminit [options] <selection>` ::

        This pass creates init constraints (for example for reset sequences) in a formal
        model.


    :code:`-seq <signal> <sequence>` ::

            Set sequence using comma-separated list of values, use 'z for
            unconstrained bits. The last value is used for the remainder of the
            trace.


    :code:`-set <signal> <value>` ::

            Add constant value constraint


    :code:`-posedge <signal>`

    :code:`-negedge <signal>` ::

            Set clock for init sequences

.. only:: latex

    ::

        
            fminit [options] <selection>
        
        This pass creates init constraints (for example for reset sequences) in a formal
        model.
        
            -seq <signal> <sequence>
                Set sequence using comma-separated list of values, use 'z for
                unconstrained bits. The last value is used for the remainder of the
                trace.
        
            -set <signal> <value>
                Add constant value constraint
        
            -posedge <signal>
            -negedge <signal>
                Set clock for init sequences
        
