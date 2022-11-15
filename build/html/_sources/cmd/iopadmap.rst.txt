======================================================
iopadmap - technology mapping of i/o pads (or buffers)
======================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help iopadmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        iopadmap [options] [selection]

    ::

        Map module inputs/outputs to PAD cells from a library. This pass
        can only map to very simple PAD cells. Use 'techmap' to further map
        the resulting cells to more sophisticated PAD cells.


    .. code:: yoscrypt

        -inpad <celltype> <in_port>[:<ext_port>]

    ::

            Map module input ports to the given cell type with the
            given output port name. if a 2nd portname is given, the
            signal is passed through the pad cell, using the 2nd
            portname as the port facing the module port.


    .. code:: yoscrypt

        -outpad <celltype> <out_port>[:<ext_port>]

   

    .. code:: yoscrypt

        -inoutpad <celltype> <io_port>[:<ext_port>]

    ::

            Similar to -inpad, but for output and inout ports.


    .. code:: yoscrypt

        -toutpad <celltype> <oe_port>:<out_port>[:<ext_port>]

    ::

            Merges $_TBUF_ cells into the output pad cell. This takes precedence
            over the other -outpad cell. The first portname is the enable input
            of the tristate driver, which can be prefixed with `~` for negative
            polarity enable.


    .. code:: yoscrypt

        -tinoutpad <celltype> <oe_port>:<in_port>:<out_port>[:<ext_port>]

    ::

            Merges $_TBUF_ cells into the inout pad cell. This takes precedence
            over the other -inoutpad cell. The first portname is the enable input
            of the tristate driver and the 2nd portname is the internal output
            buffering the external signal.  Like with `-toutpad`, the enable can
            be marked as negative polarity by prefixing the name with `~`.


    .. code:: yoscrypt

        -ignore <celltype> <portname>[:<portname>]*

    ::

            Skips mapping inputs/outputs that are already connected to given
            ports of the given cell.  Can be used multiple times.  This is in
            addition to the cells specified as mapping targets.


    .. code:: yoscrypt

        -widthparam <param_name>

    ::

            Use the specified parameter name to set the port width.


    .. code:: yoscrypt

        -nameparam <param_name>

    ::

            Use the specified parameter to set the port name.


    .. code:: yoscrypt

        -bits

    ::

            create individual bit-wide buffers even for ports that
            are wider. (the default behavior is to create word-wide
            buffers using -widthparam to set the word size on the cell.)


    ::

        Tristate PADS (-toutpad, -tinoutpad) always operate in -bits mode.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            iopadmap [options] [selection]
        
        Map module inputs/outputs to PAD cells from a library. This pass
        can only map to very simple PAD cells. Use 'techmap' to further map
        the resulting cells to more sophisticated PAD cells.
        
            -inpad <celltype> <in_port>[:<ext_port>]
                Map module input ports to the given cell type with the
                given output port name. if a 2nd portname is given, the
                signal is passed through the pad cell, using the 2nd
                portname as the port facing the module port.
        
            -outpad <celltype> <out_port>[:<ext_port>]
            -inoutpad <celltype> <io_port>[:<ext_port>]
                Similar to -inpad, but for output and inout ports.
        
            -toutpad <celltype> <oe_port>:<out_port>[:<ext_port>]
                Merges $_TBUF_ cells into the output pad cell. This takes precedence
                over the other -outpad cell. The first portname is the enable input
                of the tristate driver, which can be prefixed with `~` for negative
                polarity enable.
        
            -tinoutpad <celltype> <oe_port>:<in_port>:<out_port>[:<ext_port>]
                Merges $_TBUF_ cells into the inout pad cell. This takes precedence
                over the other -inoutpad cell. The first portname is the enable input
                of the tristate driver and the 2nd portname is the internal output
                buffering the external signal.  Like with `-toutpad`, the enable can
                be marked as negative polarity by prefixing the name with `~`.
        
            -ignore <celltype> <portname>[:<portname>]*
                Skips mapping inputs/outputs that are already connected to given
                ports of the given cell.  Can be used multiple times.  This is in
                addition to the cells specified as mapping targets.
        
            -widthparam <param_name>
                Use the specified parameter name to set the port width.
        
            -nameparam <param_name>
                Use the specified parameter to set the port name.
        
            -bits
                create individual bit-wide buffers even for ports that
                are wider. (the default behavior is to create word-wide
                buffers using -widthparam to set the word size on the cell.)
        
        Tristate PADS (-toutpad, -tinoutpad) always operate in -bits mode.
        
