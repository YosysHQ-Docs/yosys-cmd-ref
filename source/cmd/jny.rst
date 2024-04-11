===============================
jny - write design and metadata
===============================

.. raw:: latex

    \begin{comment}

.. cmd:def:: jny
    :title: write design and metadata



    .. code:: yoscrypt

        jny [options] [selection]

    ::

        Write JSON netlist metadata for the current design


    .. code:: yoscrypt

        -o <filename>

    ::

            write to the specified file.


    .. code:: yoscrypt

        -no-connections

    ::

            Don't include connection information in the netlist output.


    .. code:: yoscrypt

        -no-attributes

    ::

            Don't include attributed information in the netlist output.


    .. code:: yoscrypt

        -no-properties

    ::

            Don't include property information in the netlist output.


    ::

        See 'help write_jny' for a description of the JSON format used.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            jny [options] [selection]
        
        Write JSON netlist metadata for the current design
        
            -o <filename>
                write to the specified file.
        
            -no-connections
                Don't include connection information in the netlist output.
        
            -no-attributes
                Don't include attributed information in the netlist output.
        
            -no-properties
                Don't include property information in the netlist output.
        
        See 'help write_jny' for a description of the JSON format used.
        
