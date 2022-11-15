==========================================
setparam - set/unset parameters on objects
==========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help setparam`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        setparam [ -type cell_type ] [ -set name value | -unset name ]... [selection]

    ::

        Set/unset the given parameters on the selected cells. String values must be
        passed in double quotes (").

        The -type option can be used to change the cell type of the selected cells.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            setparam [ -type cell_type ] [ -set name value | -unset name ]... [selection]
        
        Set/unset the given parameters on the selected cells. String values must be
        passed in double quotes (").
        
        The -type option can be used to change the cell type of the selected cells.
        
