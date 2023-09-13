=====================================================
dft_tag - create tagging logic for data flow tracking
=====================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help dft_tag`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        dft_tag [options] [selection]

    ::

        This pass... TODO


    .. code:: yoscrypt

        -overwrite-only

    ::

            Only process $overwrite_tag and $original_tag cells.

    ::

        -tag-public
            For each public wire that may carry tagged data, create a new public
            wire (named <wirename>:<tagname>) that carries the tag bits. Note
            that without this, tagging logic will only be emitted as required
            for uses of $get_tag.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            dft_tag [options] [selection]
        
        This pass... TODO
        
            -overwrite-only
                Only process $overwrite_tag and $original_tag cells.
            -tag-public
                For each public wire that may carry tagged data, create a new public
                wire (named <wirename>:<tagname>) that carries the tag bits. Note
                that without this, tagging logic will only be emitted as required
                for uses of $get_tag.
        
