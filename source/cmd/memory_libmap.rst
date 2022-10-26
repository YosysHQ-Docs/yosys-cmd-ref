=====================================
memory_libmap - map memories to cells
=====================================

.. only:: html

    :code:`yosys> help memory_libmap`
    ----------------------------------------------------------------------------


    :code:`memory_libmap -lib <library_file> [-D <condition>] [selection]` ::

        This pass takes a description of available RAM cell types and maps
        all selected memories to one of them, or leaves them  to be mapped to FFs.


    :code:`-lib <library_file>` ::

          Selects a library file containing RAM cell definitions. This option
          can be passed more than once to select multiple libraries.
          See passes/memory/memlib.md for description of the library format.


    :code:`-D <condition>` ::

          Enables a condition that can be checked within the library file
          to eg. select between slightly different hardware variants.
          This option can be passed any number of times.


    :code:`-logic-cost-rom <num>`

    :code:`-logic-cost-ram <num>` ::

          Sets the cost of a single bit for memory lowered to soft logic.


    :code:`-no-auto-distributed`

    :code:`-no-auto-block`

    :code:`-no-auto-huge` ::

          Disables automatic mapping of given kind of RAMs.  Manual mapping
          (using ram_style or other attributes) is still supported.

.. only:: latex

    ::

        
            memory_libmap -lib <library_file> [-D <condition>] [selection]
        
        This pass takes a description of available RAM cell types and maps
        all selected memories to one of them, or leaves them  to be mapped to FFs.
        
          -lib <library_file>
            Selects a library file containing RAM cell definitions. This option
            can be passed more than once to select multiple libraries.
            See passes/memory/memlib.md for description of the library format.
        
          -D <condition>
            Enables a condition that can be checked within the library file
            to eg. select between slightly different hardware variants.
            This option can be passed any number of times.
        
          -logic-cost-rom <num>
          -logic-cost-ram <num>
            Sets the cost of a single bit for memory lowered to soft logic.
        
          -no-auto-distributed
          -no-auto-block
          -no-auto-huge
            Disables automatic mapping of given kind of RAMs.  Manual mapping
            (using ram_style or other attributes) is still supported.
        
