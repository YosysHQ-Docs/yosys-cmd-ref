==========================
read_blif - read BLIF file
==========================

.. raw:: latex

    \begin{comment}

.. cmd:def:: read_blif
    :title: read BLIF file



    .. code:: yoscrypt

        read_blif [options] [filename]

    ::

        Load modules from a BLIF file into the current design.


    .. code:: yoscrypt

        -sop

    ::

            Create $sop cells instead of $lut cells


    .. code:: yoscrypt

        -wideports

    ::

            Merge ports that match the pattern 'name[int]' into a single
            multi-bit port 'name'.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            read_blif [options] [filename]
        
        Load modules from a BLIF file into the current design.
        
            -sop
                Create $sop cells instead of $lut cells
        
            -wideports
                Merge ports that match the pattern 'name[int]' into a single
                multi-bit port 'name'.
        
