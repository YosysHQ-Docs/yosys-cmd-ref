============================
xprop - formal x propagation
============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help xprop`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        xprop [options] [selection]

    ::

        This pass transforms the circuit into an equivalent circuit that explicitly
        encodes the propagation of x values using purely 2-valued logic. On the
        interface between xprop-transformed and non-transformed parts of the design,
        appropriate conversions are inserted automatically.


    .. code:: yoscrypt

        -split-inputs

   

    .. code:: yoscrypt

        -split-outputs

   

    .. code:: yoscrypt

        -split-ports

    ::

            Replace each input/output/port with two new ports, one carrying the
            defined values (named <portname>_d) and one carrying the mask of which
            bits are x (named <portname>_x). When a bit in the <portname>_x is set
            the corresponding bit in <portname>_d is ignored for inputs and
            guaranteed to be 0 for outputs.


    .. code:: yoscrypt

        -assume-encoding

    ::

            Add encoding invariants as assumptions. This can speed up formal
            verification tasks.


    .. code:: yoscrypt

        -assert-encoding

    ::

            Add encoding invariants as assertions. Used for testing the xprop
            pass itself.


    .. code:: yoscrypt

        -assume-def-inputs

    ::

            Assume all inputs are fully defined. This adds corresponding
            assumptions to the design and uses these assumptions to optimize the
            xprop encoding.


    .. code:: yoscrypt

        -required

    ::

            Produce a runtime error if any encountered cell could not be encoded.


    .. code:: yoscrypt

        -formal

    ::

            Produce a runtime error if any encoded cell uses a signal that is

    ::

        neither known to be non-x nor driven by another encoded cell.


    .. code:: yoscrypt

        -debug-asserts

    ::

            Add assertions checking that the encoding used by this pass never
            produces x values within the encoded signals.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            xprop [options] [selection]
        
        This pass transforms the circuit into an equivalent circuit that explicitly
        encodes the propagation of x values using purely 2-valued logic. On the
        interface between xprop-transformed and non-transformed parts of the design,
        appropriate conversions are inserted automatically.
        
            -split-inputs
            -split-outputs
            -split-ports
                Replace each input/output/port with two new ports, one carrying the
                defined values (named <portname>_d) and one carrying the mask of which
                bits are x (named <portname>_x). When a bit in the <portname>_x is set
                the corresponding bit in <portname>_d is ignored for inputs and
                guaranteed to be 0 for outputs.
        
            -assume-encoding
                Add encoding invariants as assumptions. This can speed up formal
                verification tasks.
        
            -assert-encoding
                Add encoding invariants as assertions. Used for testing the xprop
                pass itself.
        
            -assume-def-inputs
                Assume all inputs are fully defined. This adds corresponding
                assumptions to the design and uses these assumptions to optimize the
                xprop encoding.
        
            -required
                Produce a runtime error if any encountered cell could not be encoded.
        
            -formal
                Produce a runtime error if any encoded cell uses a signal that is
        		 neither known to be non-x nor driven by another encoded cell.
        
            -debug-asserts
                Add assertions checking that the encoding used by this pass never
                produces x values within the encoded signals.
        
