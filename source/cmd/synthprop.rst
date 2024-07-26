=====================================
synthprop - synthesize SVA properties
=====================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: synthprop
    :title: synthesize SVA properties



    .. code:: yoscrypt

        synthprop [options]

    ::

        This creates synthesizable properties for the selected module.



    .. code:: yoscrypt

        -name <portname>

    ::

            name of the output port for assertions (default: assertions).


    .. code:: yoscrypt

        -map <filename>

    ::

            write the port mapping for synthesizable properties into the given file.


    .. code:: yoscrypt

        -or_outputs

    ::

            Or all outputs together to create a single output that goes high when
            any property is violated, instead of generating individual output bits.


    .. code:: yoscrypt

        -reset <portname>

    ::

            name of the top-level reset input. Latch a high state on the generated
            outputs until an asynchronous top-level reset input is activated.


    .. code:: yoscrypt

        -resetn <portname>

    ::

            like above but with inverse polarity


.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synthprop [options]
        
        This creates synthesizable properties for the selected module.
        
        
            -name <portname>
                name of the output port for assertions (default: assertions).
        
            -map <filename>
                write the port mapping for synthesizable properties into the given file.
        
            -or_outputs
                Or all outputs together to create a single output that goes high when
                any property is violated, instead of generating individual output bits.
        
            -reset <portname>
                name of the top-level reset input. Latch a high state on the generated
                outputs until an asynchronous top-level reset input is activated.
        
            -resetn <portname>
                like above but with inverse polarity
        
        
