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

        This creates synthesizable properties for selected module.



    .. code:: yoscrypt

        -name <portname>

   

    ::

        Name output port for assertions (default: assertions).

    .. code:: yoscrypt

        -map <filename>

   

    ::

        Write port mapping for synthesizable properties.

    .. code:: yoscrypt

        -or_outputs

   

    ::

        Or all outputs together to create a single output that goes high when any ::

        property is violated, instead of generating individual output bits.



    .. code:: yoscrypt

        -reset <portname>

   

    ::

        Name of top-level reset input. Latch a high state on the generated outputs ::

        until an asynchronous top-level reset input is activated.



    .. code:: yoscrypt

        -resetn <portname>

   

    ::

        Name of top-level reset input (inverse polarity). Latch a high state on the ::

        generated outputs until an asynchronous top-level reset input is activated.


.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            synthprop [options]
        
        This creates synthesizable properties for selected module.
        
        
            -name <portname>
        
        Name output port for assertions (default: assertions).
        
        
            -map <filename>
        
        Write port mapping for synthesizable properties.
        
        
            -or_outputs
        
        Or all outputs together to create a single output that goes high when any
        property is violated, instead of generating individual output bits.
        
        
            -reset <portname>
        
        Name of top-level reset input. Latch a high state on the generated outputs
        until an asynchronous top-level reset input is activated.
        
        
            -resetn <portname>
        
        Name of top-level reset input (inverse polarity). Latch a high state on the
        generated outputs until an asynchronous top-level reset input is activated.
        
        
