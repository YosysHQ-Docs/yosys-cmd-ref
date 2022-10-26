=========================================
setattr - set/unset attributes on objects
=========================================

.. only:: html

    :code:`yosys> help setattr`
    ----------------------------------------------------------------------------


    :code:`setattr [ -mod ] [ -set name value | -unset name ]... [selection]` ::

        Set/unset the given attributes on the selected objects. String values must be
        passed in double quotes (").

        When called with -mod, this command will set and unset attributes on modules
        instead of objects within modules.

.. only:: latex

    ::

        
            setattr [ -mod ] [ -set name value | -unset name ]... [selection]
        
        Set/unset the given attributes on the selected objects. String values must be
        passed in double quotes (").
        
        When called with -mod, this command will set and unset attributes on modules
        instead of objects within modules.
        
