======================================
write_btor - write design to BTOR file
======================================

.. only:: html

    :code:`yosys> help write_btor`
    ----------------------------------------------------------------------------


    :code:`write_btor [options] [filename]` ::

        Write a BTOR description of the current design.


    :code:`-v` ::

          Add comments and indentation to BTOR output file


    :code:`-s` ::

          Output only a single bad property for all asserts


    :code:`-c` ::

          Output cover properties using 'bad' statements instead of asserts


    :code:`-i <filename>` ::

          Create additional info file with auxiliary information


    :code:`-x` ::

          Output symbols for internal netnames (starting with '$')

.. only:: latex

    ::

        
            write_btor [options] [filename]
        
        Write a BTOR description of the current design.
        
          -v
            Add comments and indentation to BTOR output file
        
          -s
            Output only a single bad property for all asserts
        
          -c
            Output cover properties using 'bad' statements instead of asserts
        
          -i <filename>
            Create additional info file with auxiliary information
        
          -x
            Output symbols for internal netnames (starting with '$')
        
