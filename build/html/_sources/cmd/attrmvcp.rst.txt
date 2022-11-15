==============================================================
attrmvcp - move or copy attributes from wires to driving cells
==============================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help attrmvcp`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        attrmvcp [options] [selection]

    ::

        Move or copy attributes on wires to the cells driving them.


    .. code:: yoscrypt

        -copy

    ::

            By default, attributes are moved. This will only add
            the attribute to the cell, without removing it from
            the wire.


    .. code:: yoscrypt

        -purge

    ::

            If no selected cell consumes the attribute, then it is
            left on the wire by default. This option will cause the
            attribute to be removed from the wire, even if no selected
            cell takes it.


    .. code:: yoscrypt

        -driven

    ::

            By default, attriburtes are moved to the cell driving the
            wire. With this option set it will be moved to the cell
            driven by the wire instead.


    .. code:: yoscrypt

        -attr <attrname>

    ::

            Move or copy this attribute. This option can be used
            multiple times.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            attrmvcp [options] [selection]
        
        Move or copy attributes on wires to the cells driving them.
        
            -copy
                By default, attributes are moved. This will only add
                the attribute to the cell, without removing it from
                the wire.
        
            -purge
                If no selected cell consumes the attribute, then it is
                left on the wire by default. This option will cause the
                attribute to be removed from the wire, even if no selected
                cell takes it.
        
            -driven
                By default, attriburtes are moved to the cell driving the
                wire. With this option set it will be moved to the cell
                driven by the wire instead.
        
            -attr <attrname>
                Move or copy this attribute. This option can be used
                multiple times.
        
