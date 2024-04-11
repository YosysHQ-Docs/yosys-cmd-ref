========================================
nlutmap - map to LUTs of different sizes
========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: nlutmap
    :title: map to LUTs of different sizes



    .. code:: yoscrypt

        nlutmap [options] [selection]

    ::

        This pass uses successive calls to 'abc' to map to an architecture. That
        provides a small number of differently sized LUTs.


    .. code:: yoscrypt

        -luts N_1,N_2,N_3,...

    ::

            The number of LUTs with 1, 2, 3, ... inputs that are
            available in the target architecture.


    .. code:: yoscrypt

        -assert

    ::

            Create an error if not all logic can be mapped


    ::

        Excess logic that does not fit into the specified LUTs is mapped back
        to generic logic gates ($_AND_, etc.).

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            nlutmap [options] [selection]
        
        This pass uses successive calls to 'abc' to map to an architecture. That
        provides a small number of differently sized LUTs.
        
            -luts N_1,N_2,N_3,...
                The number of LUTs with 1, 2, 3, ... inputs that are
                available in the target architecture.
        
            -assert
                Create an error if not all logic can be mapped
        
        Excess logic that does not fit into the specified LUTs is mapped back
        to generic logic gates ($_AND_, etc.).
        
