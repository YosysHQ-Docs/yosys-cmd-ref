==============================================================
hilomap - technology mapping of constant hi- and/or lo-drivers
==============================================================

.. only:: html

    :code:`yosys> help hilomap`
    ----------------------------------------------------------------------------


    :code:`hilomap [options] [selection]` ::

        Map constants to 'tielo' and 'tiehi' driver cells.


    :code:`-hicell <celltype> <portname>` ::

            Replace constant hi bits with this cell.


    :code:`-locell <celltype> <portname>` ::

            Replace constant lo bits with this cell.


    :code:`-singleton` ::

            Create only one hi/lo cell and connect all constant bits
            to that cell. Per default a separate cell is created for
            each constant bit.

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
        
