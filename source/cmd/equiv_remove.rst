==================================
equiv_remove - remove $equiv cells
==================================

.. only:: html

    :code:`yosys> help equiv_remove`
    ----------------------------------------------------------------------------


    :code:`equiv_remove [options] [selection]` ::

        This command removes the selected $equiv cells. If neither -gold nor -gate is
        used then only proven cells are removed.


    :code:`-gold` ::

            keep gold circuit


    :code:`-gate` ::

            keep gate circuit

.. only:: latex

    ::

        
            equiv_remove [options] [selection]
        
        This command removes the selected $equiv cells. If neither -gold nor -gate is
        used then only proven cells are removed.
        
            -gold
                keep gold circuit
        
            -gate
                keep gate circuit
        
