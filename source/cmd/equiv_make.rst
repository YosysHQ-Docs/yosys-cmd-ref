=======================================================
equiv_make - prepare a circuit for equivalence checking
=======================================================

.. only:: html

    :code:`yosys> help equiv_make`
    ----------------------------------------------------------------------------


    :code:`equiv_make [options] gold_module gate_module equiv_module` ::

        This creates a module annotated with $equiv cells from two presumably
        equivalent modules. Use commands such as 'equiv_simple' and 'equiv_status'
        to work with the created equivalent checking module.


    :code:`-inames` ::

            Also match cells and wires with $... names.


    :code:`-blacklist <file>` ::

            Do not match cells or signals that match the names in the file.


    :code:`-encfile <file>` ::

            Match FSM encodings using the description from the file.
            See 'help fsm_recode' for details.


    ::

        Note: The circuit created by this command is not a miter (with something like
        a trigger output), but instead uses $equiv cells to encode the equivalence
        checking problem. Use 'miter -equiv' if you want to create a miter circuit.

.. only:: latex

    ::

        
            equiv_make [options] gold_module gate_module equiv_module
        
        This creates a module annotated with $equiv cells from two presumably
        equivalent modules. Use commands such as 'equiv_simple' and 'equiv_status'
        to work with the created equivalent checking module.
        
            -inames
                Also match cells and wires with $... names.
        
            -blacklist <file>
                Do not match cells or signals that match the names in the file.
        
            -encfile <file>
                Match FSM encodings using the description from the file.
                See 'help fsm_recode' for details.
        
        Note: The circuit created by this command is not a miter (with something like
        a trigger output), but instead uses $equiv cells to encode the equivalence
        checking problem. Use 'miter -equiv' if you want to create a miter circuit.
        
