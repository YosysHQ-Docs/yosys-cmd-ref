====================================
write_jny - generate design metadata
====================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_jny`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        jny [options] [selection]

    ::

        Write JSON netlist metadata for the current design


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

        The JSON schema for JNY output files is located in the "jny.schema.json" file
        which is located at "https://raw.githubusercontent.com/YosysHQ/yosys/master/misc/jny.schema.json"

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            jny [options] [selection]
        
        Write JSON netlist metadata for the current design
        
            -no-connections
                Don't include connection information in the netlist output.
        
            -no-attributes
                Don't include attributed information in the netlist output.
        
            -no-properties
                Don't include property information in the netlist output.
        
        The JSON schema for JNY output files is located in the "jny.schema.json" file
        which is located at "https://raw.githubusercontent.com/YosysHQ/yosys/master/misc/jny.schema.json"
        
