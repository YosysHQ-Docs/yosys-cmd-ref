=============================================
fminit - set init values/sequences for formal
=============================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: fminit
    :title: set init values/sequences for formal



    .. code:: yoscrypt

        fminit [options] <selection>

    ::

        This pass creates init constraints (for example for reset sequences) in a formal
        model.


    .. code:: yoscrypt

        -seq <signal> <sequence>

    ::

            Set sequence using comma-separated list of values, use 'z for
            unconstrained bits. The last value is used for the remainder of the
            trace.


    .. code:: yoscrypt

        -set <signal> <value>

    ::

            Add constant value constraint


    .. code:: yoscrypt

        -posedge <signal>

   

    .. code:: yoscrypt

        -negedge <signal>

    ::

            Set clock for init sequences

.. raw:: latex

    \end{comment}

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
        
