=====================================
splitcells - split up multi-bit cells
=====================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: splitcells
    :title: split up multi-bit cells



    .. code:: yoscrypt

        splitcells [options] [selection]

    ::

        This command splits multi-bit cells into smaller chunks, based on usage of the
        cell output bits.

        This command operates only in cells such as $or, $and, and $mux, that are easily
        cut into bit-slices.


    .. code:: yoscrypt

        -format char1[char2[char3]]

    ::

            the first char is inserted between the cell name and the bit index, the
            second char is appended to the cell name. e.g. -format () creates cell
            names like 'mycell(42)'. the 3rd character is the range separation
            character when creating multi-bit cells. the default is '[]:'.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            splitcells [options] [selection]
        
        This command splits multi-bit cells into smaller chunks, based on usage of the
        cell output bits.
        
        This command operates only in cells such as $or, $and, and $mux, that are easily
        cut into bit-slices.
        
            -format char1[char2[char3]]
                the first char is inserted between the cell name and the bit index, the
                second char is appended to the cell name. e.g. -format () creates cell
                names like 'mycell(42)'. the 3rd character is the range separation
                character when creating multi-bit cells. the default is '[]:'.
        
