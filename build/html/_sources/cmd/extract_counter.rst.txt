=================================================
extract_counter - Extract GreenPak4 counter cells
=================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help extract_counter`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        extract_counter [options] [selection]

    ::

        This pass converts non-resettable or async resettable down counters to
        counter cells. Use a target-specific 'techmap' map file to convert those cells
        to the actual target cells.


    .. code:: yoscrypt

        -maxwidth N

    ::

            Only extract counters up to N bits wide (default 64)


    .. code:: yoscrypt

        -minwidth N

    ::

            Only extract counters at least N bits wide (default 2)


    .. code:: yoscrypt

        -allow_arst yes|no

    ::

            Allow counters to have async reset (default yes)


    .. code:: yoscrypt

        -dir up|down|both

    ::

            Look for up-counters, down-counters, or both (default down)


    .. code:: yoscrypt

        -pout X,Y,...

    ::

            Only allow parallel output from the counter to the listed cell types
            (if not specified, parallel outputs are not restricted)


.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            extract_counter [options] [selection]
        
        This pass converts non-resettable or async resettable down counters to
        counter cells. Use a target-specific 'techmap' map file to convert those cells
        to the actual target cells.
        
            -maxwidth N
                Only extract counters up to N bits wide (default 64)
        
            -minwidth N
                Only extract counters at least N bits wide (default 2)
        
            -allow_arst yes|no
                Allow counters to have async reset (default yes)
        
            -dir up|down|both
                Look for up-counters, down-counters, or both (default down)
        
            -pout X,Y,...
                Only allow parallel output from the counter to the listed cell types
                (if not specified, parallel outputs are not restricted)
        
        
