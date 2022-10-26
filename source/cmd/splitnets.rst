===================================
splitnets - split up multi-bit nets
===================================

.. only:: html

    :code:`yosys> help splitnets`
    ----------------------------------------------------------------------------


    :code:`splitnets [options] [selection]` ::

        This command splits multi-bit nets into single-bit nets.


    :code:`-format char1[char2[char3]]` ::

            the first char is inserted between the net name and the bit index, the
            second char is appended to the netname. e.g. -format () creates net
            names like 'mysignal(42)'. the 3rd character is the range separation
            character when creating multi-bit wires. the default is '[]:'.


    :code:`-ports` ::

            also split module ports. per default only internal signals are split.


    :code:`-driver` ::

            don't blindly split nets in individual bits. instead look at the driver
            and split nets so that no driver drives only part of a net.

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
        
