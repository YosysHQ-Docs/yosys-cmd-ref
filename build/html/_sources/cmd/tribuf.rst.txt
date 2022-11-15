================================
tribuf - infer tri-state buffers
================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help tribuf`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        tribuf [options] [selection]

    ::

        This pass transforms $mux cells with 'z' inputs to tristate buffers.


    .. code:: yoscrypt

        -merge

    ::

            merge multiple tri-state buffers driving the same net
            into a single buffer.


    .. code:: yoscrypt

        -logic

    ::

            convert tri-state buffers that do not drive output ports
            to non-tristate logic. this option implies -merge.


    .. code:: yoscrypt

        -formal

    ::

            convert all tri-state buffers to non-tristate logic and
            add a formal assertion that no two buffers are driving the
            same net simultaneously. this option implies -merge.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            tribuf [options] [selection]
        
        This pass transforms $mux cells with 'z' inputs to tristate buffers.
        
            -merge
                merge multiple tri-state buffers driving the same net
                into a single buffer.
        
            -logic
                convert tri-state buffers that do not drive output ports
                to non-tristate logic. this option implies -merge.
        
            -formal
                convert all tri-state buffers to non-tristate logic and
                add a formal assertion that no two buffers are driving the
                same net simultaneously. this option implies -merge.
        
