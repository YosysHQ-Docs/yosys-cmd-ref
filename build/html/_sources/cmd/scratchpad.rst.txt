=============================================
scratchpad - get/set values in the scratchpad
=============================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help scratchpad`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        scratchpad [options]

    ::

        This pass allows to read and modify values from the scratchpad of the current
        design. Options:


    .. code:: yoscrypt

        -get <identifier>

    ::

            print the value saved in the scratchpad under the given identifier.


    .. code:: yoscrypt

        -set <identifier> <value>

    ::

            save the given value in the scratchpad under the given identifier.


    .. code:: yoscrypt

        -unset <identifier>

    ::

            remove the entry for the given identifier from the scratchpad.


    .. code:: yoscrypt

        -copy <identifier_from> <identifier_to>

    ::

            copy the value of the first identifier to the second identifier.


    .. code:: yoscrypt

        -assert <identifier> <value>

    ::

            assert that the entry for the given identifier is set to the given
            value.


    .. code:: yoscrypt

        -assert-set <identifier>

    ::

            assert that the entry for the given identifier exists.


    .. code:: yoscrypt

        -assert-unset <identifier>

    ::

            assert that the entry for the given identifier does not exist.


    ::

        The identifier may not contain whitespace. By convention, it is usually prefixed
        by the name of the pass that uses it, e.g. 'opt.did_something'. If the value
        contains whitespace, it must be enclosed in double quotes.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            scratchpad [options]
        
        This pass allows to read and modify values from the scratchpad of the current
        design. Options:
        
            -get <identifier>
                print the value saved in the scratchpad under the given identifier.
        
            -set <identifier> <value>
                save the given value in the scratchpad under the given identifier.
        
            -unset <identifier>
                remove the entry for the given identifier from the scratchpad.
        
            -copy <identifier_from> <identifier_to>
                copy the value of the first identifier to the second identifier.
        
            -assert <identifier> <value>
                assert that the entry for the given identifier is set to the given
                value.
        
            -assert-set <identifier>
                assert that the entry for the given identifier exists.
        
            -assert-unset <identifier>
                assert that the entry for the given identifier does not exist.
        
        The identifier may not contain whitespace. By convention, it is usually prefixed
        by the name of the pass that uses it, e.g. 'opt.did_something'. If the value
        contains whitespace, it must be enclosed in double quotes.
        
