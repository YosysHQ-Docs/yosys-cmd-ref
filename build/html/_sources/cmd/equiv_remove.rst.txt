==================================
equiv_remove - remove $equiv cells
==================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help equiv_remove`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        equiv_remove [options] [selection]

    ::

        This command removes the selected $equiv cells. If neither -gold nor -gate is
        used then only proven cells are removed.


    .. code:: yoscrypt

        -gold

    ::

            keep gold circuit


    .. code:: yoscrypt

        -gate

    ::

            keep gate circuit

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            equiv_remove [options] [selection]
        
        This command removes the selected $equiv cells. If neither -gold nor -gate is
        used then only proven cells are removed.
        
            -gold
                keep gold circuit
        
            -gate
                keep gate circuit
        
