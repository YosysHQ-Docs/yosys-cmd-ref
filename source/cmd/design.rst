===============================================
design - save, restore and reset current design
===============================================

.. only:: html

    :code:`yosys> help design`
    ----------------------------------------------------------------------------


    :code:`design -reset` ::

        Clear the current design.



    :code:`design -save <name>` ::

        Save the current design under the given name.



    :code:`design -stash <name>` ::

        Save the current design under the given name and then clear the current design.



    :code:`design -push` ::

        Push the current design to the stack and then clear the current design.



    :code:`design -push-copy` ::

        Push the current design to the stack without clearing the current design.



    :code:`design -pop` ::

        Reset the current design and pop the last design from the stack.



    :code:`design -load <name>` ::

        Reset the current design and load the design previously saved under the given
        name.



    :code:`design -copy-from <name> [-as <new_mod_name>] <selection>` ::

        Copy modules from the specified design into the current one. The selection is
        evaluated in the other design.



    :code:`design -copy-to <name> [-as <new_mod_name>] [selection]` ::

        Copy modules from the current design into the specified one.



    :code:`design -import <name> [-as <new_top_name>] [selection]` ::

        Import the specified design into the current design. The source design must
        either have a selected top module or the selection must contain exactly one
        module that is then used as top module for this command.



    :code:`design -reset-vlog` ::

        The Verilog front-end remembers defined macros and top-level declarations
        between calls to 'read_verilog'. This command resets this memory.

            design -delete <name>

        Delete the design previously saved under the given name.

.. only:: latex

    ::

        
            design -reset
        
        Clear the current design.
        
        
            design -save <name>
        
        Save the current design under the given name.
        
        
            design -stash <name>
        
        Save the current design under the given name and then clear the current design.
        
        
            design -push
        
        Push the current design to the stack and then clear the current design.
        
        
            design -push-copy
        
        Push the current design to the stack without clearing the current design.
        
        
            design -pop
        
        Reset the current design and pop the last design from the stack.
        
        
            design -load <name>
        
        Reset the current design and load the design previously saved under the given
        name.
        
        
            design -copy-from <name> [-as <new_mod_name>] <selection>
        
        Copy modules from the specified design into the current one. The selection is
        evaluated in the other design.
        
        
            design -copy-to <name> [-as <new_mod_name>] [selection]
        
        Copy modules from the current design into the specified one.
        
        
            design -import <name> [-as <new_top_name>] [selection]
        
        Import the specified design into the current design. The source design must
        either have a selected top module or the selection must contain exactly one
        module that is then used as top module for this command.
        
        
            design -reset-vlog
        
        The Verilog front-end remembers defined macros and top-level declarations
        between calls to 'read_verilog'. This command resets this memory.
        
            design -delete <name>
        
        Delete the design previously saved under the given name.
        
