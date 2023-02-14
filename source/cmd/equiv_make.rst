=======================================================
equiv_make - prepare a circuit for equivalence checking
=======================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help equiv_make`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        equiv_make [options] gold_module gate_module equiv_module

    ::

        This creates a module annotated with $equiv cells from two presumably
        equivalent modules. Use commands such as 'equiv_simple' and 'equiv_status'
        to work with the created equivalent checking module.


    .. code:: yoscrypt

        -inames

    ::

            Also match cells and wires with $... names.


    .. code:: yoscrypt

        -blacklist <file>

    ::

            Do not match cells or signals that match the names in the file.


    .. code:: yoscrypt

        -encfile <file>

    ::

            Match FSM encodings using the description from the file.
            See 'help fsm_recode' for details.


    .. code:: yoscrypt

        -make_assert

    ::

            Check equivalence with $assert cells instead of $equiv.
            $eqx (===) is used to compare signals.

    ::

        Note: The circuit created by this command is not a miter (with something like
        a trigger output), but instead uses $equiv cells to encode the equivalence
        checking problem. Use 'miter -equiv' if you want to create a miter circuit.

.. raw:: latex

    \end{comment}

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
        
            -make_assert
                Check equivalence with $assert cells instead of $equiv.
                $eqx (===) is used to compare signals.
        Note: The circuit created by this command is not a miter (with something like
        a trigger output), but instead uses $equiv cells to encode the equivalence
        checking problem. Use 'miter -equiv' if you want to create a miter circuit.
        
