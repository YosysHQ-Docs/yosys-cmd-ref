===========================================
cd - a shortcut for 'select -module <name>'
===========================================

.. only:: html

    :code:`yosys> help cd`
    ----------------------------------------------------------------------------


    :code:`cd <modname>` ::

        This is just a shortcut for 'select -module <modname>'.



    :code:`cd <cellname>` ::

        When no module with the specified name is found, but there is a cell
        with the specified name in the current module, then this is equivalent
        to 'cd <celltype>'.



    :code:`cd ..` ::

        Remove trailing substrings that start with '.' in current module name until
        the name of a module in the current design is generated, then switch to that
        module. Otherwise clear the current selection.



    :code:`cd` ::

        This is just a shortcut for 'select -clear'.

.. only:: latex

    ::

        
            cd <modname>
        
        This is just a shortcut for 'select -module <modname>'.
        
        
            cd <cellname>
        
        When no module with the specified name is found, but there is a cell
        with the specified name in the current module, then this is equivalent
        to 'cd <celltype>'.
        
        
            cd ..
        
        Remove trailing substrings that start with '.' in current module name until
        the name of a module in the current design is generated, then switch to that
        module. Otherwise clear the current selection.
        
        
            cd
        
        This is just a shortcut for 'select -clear'.
        
