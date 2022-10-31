=====================================
delete - delete objects in the design
=====================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help delete`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        delete [selection]

    ::

        Deletes the selected objects. This will also remove entire modules, if the
        whole module is selected.


    .. code:: yoscrypt

        delete {-input|-output|-port} [selection]

    ::

        Does not delete any object but removes the input and/or output flag on the
        selected wires, thus 'deleting' module ports.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            delete [selection]
        
        Deletes the selected objects. This will also remove entire modules, if the
        whole module is selected.
        
        
            delete {-input|-output|-port} [selection]
        
        Does not delete any object but removes the input and/or output flag on the
        selected wires, thus 'deleting' module ports.
        
