==========================
read_blif - read BLIF file
==========================

.. only:: html

    :code:`yosys> help read_blif`
    ----------------------------------------------------------------------------


    :code:`read_blif [options] [filename]` ::

        Load modules from a BLIF file into the current design.


    :code:`-sop` ::

            Create $sop cells instead of $lut cells


    :code:`-wideports` ::

            Merge ports that match the pattern 'name[int]' into a single
            multi-bit port 'name'.

.. only:: latex

    ::

        
            read_blif [options] [filename]
        
        Load modules from a BLIF file into the current design.
        
            -sop
                Create $sop cells instead of $lut cells
        
            -wideports
                Merge ports that match the pattern 'name[int]' into a single
                multi-bit port 'name'.
        
