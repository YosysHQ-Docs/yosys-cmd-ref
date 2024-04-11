==============================================================
hilomap - technology mapping of constant hi- and/or lo-drivers
==============================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: hilomap
    :title: technology mapping of constant hi- and/or lo-drivers



    .. code:: yoscrypt

        hilomap [options] [selection]

    ::

        Map constants to 'tielo' and 'tiehi' driver cells.


    .. code:: yoscrypt

        -hicell <celltype> <portname>

    ::

            Replace constant hi bits with this cell.


    .. code:: yoscrypt

        -locell <celltype> <portname>

    ::

            Replace constant lo bits with this cell.


    .. code:: yoscrypt

        -singleton

    ::

            Create only one hi/lo cell and connect all constant bits
            to that cell. Per default a separate cell is created for
            each constant bit.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            hilomap [options] [selection]
        
        Map constants to 'tielo' and 'tiehi' driver cells.
        
            -hicell <celltype> <portname>
                Replace constant hi bits with this cell.
        
            -locell <celltype> <portname>
                Replace constant lo bits with this cell.
        
            -singleton
                Create only one hi/lo cell and connect all constant bits
                to that cell. Per default a separate cell is created for
                each constant bit.
        
