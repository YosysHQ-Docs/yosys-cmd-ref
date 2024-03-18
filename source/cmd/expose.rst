=================================================
expose - convert internal signals to module ports
=================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: expose
    :title: convert internal signals to module ports



    .. code:: yoscrypt

        expose [options] [selection]

    ::

        This command exposes all selected internal signals of a module as additional
        outputs.


    .. code:: yoscrypt

        -dff

    ::

            only consider wires that are directly driven by register cell.


    .. code:: yoscrypt

        -cut

    ::

            when exposing a wire, create an input/output pair and cut the internal
            signal path at that wire.


    .. code:: yoscrypt

        -input

    ::

            when exposing a wire, create an input port and disconnect the internal
            driver.


    .. code:: yoscrypt

        -shared

    ::

            only expose those signals that are shared among the selected modules.
            this is useful for preparing modules for equivalence checking.


    .. code:: yoscrypt

        -evert

    ::

            also turn connections to instances of other modules to additional
            inputs and outputs and remove the module instances.


    .. code:: yoscrypt

        -evert-dff

    ::

            turn flip-flops to sets of inputs and outputs.


    .. code:: yoscrypt

        -sep <separator>

    ::

            when creating new wire/port names, the original object name is suffixed
            with this separator (default: '.') and the port name or a type
            designator for the exposed signal.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            expose [options] [selection]
        
        This command exposes all selected internal signals of a module as additional
        outputs.
        
            -dff
                only consider wires that are directly driven by register cell.
        
            -cut
                when exposing a wire, create an input/output pair and cut the internal
                signal path at that wire.
        
            -input
                when exposing a wire, create an input port and disconnect the internal
                driver.
        
            -shared
                only expose those signals that are shared among the selected modules.
                this is useful for preparing modules for equivalence checking.
        
            -evert
                also turn connections to instances of other modules to additional
                inputs and outputs and remove the module instances.
        
            -evert-dff
                turn flip-flops to sets of inputs and outputs.
        
            -sep <separator>
                when creating new wire/port names, the original object name is suffixed
                with this separator (default: '.') and the port name or a type
                designator for the exposed signal.
        
