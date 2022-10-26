================================================
check - check for obvious problems in the design
================================================

.. only:: html

    :code:`yosys> help check`
    ----------------------------------------------------------------------------


    :code:`check [options] [selection]` ::

        This pass identifies the following problems in the current design:

          - combinatorial loops
          - two or more conflicting drivers for one wire
          - used wires that do not have a driver

        Options:


    :code:`-noinit` ::

            also check for wires which have the 'init' attribute set


    :code:`-initdrv` ::

            also check for wires that have the 'init' attribute set and are not
            driven by an FF cell type


    :code:`-mapped` ::

            also check for internal cells that have not been mapped to cells of the
            target architecture


    :code:`-allow-tbuf` ::

            modify the -mapped behavior to still allow $_TBUF_ cells


    :code:`-assert` ::

            produce a runtime error if any problems are found in the current design

.. only:: latex

    ::

        
            check [options] [selection]
        
        This pass identifies the following problems in the current design:
        
          - combinatorial loops
          - two or more conflicting drivers for one wire
          - used wires that do not have a driver
        
        Options:
        
            -noinit
                also check for wires which have the 'init' attribute set
        
            -initdrv
                also check for wires that have the 'init' attribute set and are not
                driven by an FF cell type
        
            -mapped
                also check for internal cells that have not been mapped to cells of the
                target architecture
        
            -allow-tbuf
                modify the -mapped behavior to still allow $_TBUF_ cells
        
            -assert
                produce a runtime error if any problems are found in the current design
        
