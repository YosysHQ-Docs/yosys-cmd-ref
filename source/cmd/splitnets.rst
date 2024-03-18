===================================
splitnets - split up multi-bit nets
===================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: splitnets
    :title: split up multi-bit nets



    .. code:: yoscrypt

        splitnets [options] [selection]

    ::

        This command splits multi-bit nets into single-bit nets.


    .. code:: yoscrypt

        -format char1[char2[char3]]

    ::

            the first char is inserted between the net name and the bit index, the
            second char is appended to the netname. e.g. -format () creates net
            names like 'mysignal(42)'. the 3rd character is the range separation
            character when creating multi-bit wires. the default is '[]:'.


    .. code:: yoscrypt

        -ports

    ::

            also split module ports. per default only internal signals are split.


    .. code:: yoscrypt

        -driver

    ::

            don't blindly split nets in individual bits. instead look at the driver
            and split nets so that no driver drives only part of a net.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            splitnets [options] [selection]
        
        This command splits multi-bit nets into single-bit nets.
        
            -format char1[char2[char3]]
                the first char is inserted between the net name and the bit index, the
                second char is appended to the netname. e.g. -format () creates net
                names like 'mysignal(42)'. the 3rd character is the range separation
                character when creating multi-bit wires. the default is '[]:'.
        
            -ports
                also split module ports. per default only internal signals are split.
        
            -driver
                don't blindly split nets in individual bits. instead look at the driver
                and split nets so that no driver drives only part of a net.
        
