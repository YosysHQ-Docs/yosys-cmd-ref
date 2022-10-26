=====================================
delete - delete objects in the design
=====================================

.. only:: html

    :code:`yosys> help delete`
    ----------------------------------------------------------------------------


    :code:`delete [selection]` ::

        Deletes the selected objects. This will also remove entire modules, if the
        whole module is selected.



    :code:`delete {-input|-output|-port} [selection]` ::

        Does not delete any object but removes the input and/or output flag on the
        selected wires, thus 'deleting' module ports.

.. only:: latex

    ::

        
            delete [selection]
        
        Deletes the selected objects. This will also remove entire modules, if the
        whole module is selected.
        
        
            delete {-input|-output|-port} [selection]
        
        Does not delete any object but removes the input and/or output flag on the
        selected wires, thus 'deleting' module ports.
        
