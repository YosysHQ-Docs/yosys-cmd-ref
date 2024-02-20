============================================
dfflibmap - technology mapping of flip-flops
============================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help dfflibmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        dfflibmap [-prepare] [-map-only] [-info] [-dont_use <cell_name>] -liberty <file> [selection]

    ::

        Map internal flip-flop cells to the flip-flop cells in the technology
        library specified in the given liberty file.

        This pass may add inverters as needed. Therefore it is recommended to
        first run this pass and then map the logic paths to the target technology.

        When called with -prepare, this command will convert the internal FF cells
        to the internal cell types that best match the cells found in the given
        liberty file, but won't actually map them to the target cells.

        When called with -map-only, this command will only map internal cell
        types that are already of exactly the right type to match the target
        cells, leaving remaining internal cells untouched.

        When called with -info, this command will only print the target cell
        list, along with their associated internal cell types, and the arguments
        that would be passed to the dfflegalize pass.  The design will not be
        changed.

        When called with -dont_use, this command will not map to the specified cell
        name as an alternative to setting the dont_use property in the Liberty file.
        This argument can be called multiple times with different cell names. This
        argument also supports simple glob patterns in the cell name.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            dfflibmap [-prepare] [-map-only] [-info] [-dont_use <cell_name>] -liberty <file> [selection]
        
        Map internal flip-flop cells to the flip-flop cells in the technology
        library specified in the given liberty file.
        
        This pass may add inverters as needed. Therefore it is recommended to
        first run this pass and then map the logic paths to the target technology.
        
        When called with -prepare, this command will convert the internal FF cells
        to the internal cell types that best match the cells found in the given
        liberty file, but won't actually map them to the target cells.
        
        When called with -map-only, this command will only map internal cell
        types that are already of exactly the right type to match the target
        cells, leaving remaining internal cells untouched.
        
        When called with -info, this command will only print the target cell
        list, along with their associated internal cell types, and the arguments
        that would be passed to the dfflegalize pass.  The design will not be
        changed.
        
        When called with -dont_use, this command will not map to the specified cell
        name as an alternative to setting the dont_use property in the Liberty file.
        This argument can be called multiple times with different cell names. This
        argument also supports simple glob patterns in the cell name.
        
