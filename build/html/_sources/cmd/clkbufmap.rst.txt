==================================================
clkbufmap - insert clock buffers on clock networks
==================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help clkbufmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        clkbufmap [options] [selection]

    ::

        Inserts clock buffers between nets connected to clock inputs and their drivers.

        In the absence of any selection, all wires without the 'clkbuf_inhibit'
        attribute will be considered for clock buffer insertion.
        Alternatively, to consider all wires without the 'buffer_type' attribute set to
        'none' or 'bufr' one would specify:
          'w:* a:buffer_type=none a:buffer_type=bufr %u %d'
        as the selection.


    .. code:: yoscrypt

        -buf <celltype> <portname_out>:<portname_in>

    ::

            Specifies the cell type to use for the clock buffers
            and its port names.  The first port will be connected to
            the clock network sinks, and the second will be connected
            to the actual clock source.


    .. code:: yoscrypt

        -inpad <celltype> <portname_out>:<portname_in>

    ::

            If specified, a PAD cell of the given type is inserted on
            clock nets that are also top module's inputs (in addition
            to the clock buffer, if any).


    ::

        At least one of -buf or -inpad should be specified.
.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            clkbufmap [options] [selection]
        
        Inserts clock buffers between nets connected to clock inputs and their drivers.
        
        In the absence of any selection, all wires without the 'clkbuf_inhibit'
        attribute will be considered for clock buffer insertion.
        Alternatively, to consider all wires without the 'buffer_type' attribute set to
        'none' or 'bufr' one would specify:
          'w:* a:buffer_type=none a:buffer_type=bufr %u %d'
        as the selection.
        
            -buf <celltype> <portname_out>:<portname_in>
                Specifies the cell type to use for the clock buffers
                and its port names.  The first port will be connected to
                the clock network sinks, and the second will be connected
                to the actual clock source.
        
            -inpad <celltype> <portname_out>:<portname_in>
                If specified, a PAD cell of the given type is inserted on
                clock nets that are also top module's inputs (in addition
                to the clock buffer, if any).
        
        At least one of -buf or -inpad should be specified.
