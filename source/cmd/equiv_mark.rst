==============================================
equiv_mark - mark equivalence checking regions
==============================================

.. only:: html

    :code:`yosys> help equiv_mark`
    ----------------------------------------------------------------------------


    :code:`equiv_mark [options] [selection]` ::

        This command marks the regions in an equivalence checking module. Region 0 is
        the proven part of the circuit. Regions with higher numbers are connected
        unproven subcricuits. The integer attribute 'equiv_region' is set on all
        wires and cells.

.. only:: latex

    ::

        
            equiv_mark [options] [selection]
        
        This command marks the regions in an equivalence checking module. Region 0 is
        the proven part of the circuit. Regions with higher numbers are connected
        unproven subcricuits. The integer attribute 'equiv_region' is set on all
        wires and cells.
        
