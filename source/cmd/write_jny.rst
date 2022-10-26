====================================
write_jny - generate design metadata
====================================

.. only:: html

    :code:`yosys> help write_jny`
    ----------------------------------------------------------------------------


    :code:`jny [options] [selection]` ::

        Write JSON netlist metadata for the current design


    :code:`-no-connections` ::

            Don't include connection information in the netlist output.


    :code:`-no-attributes` ::

            Don't include attributed information in the netlist output.


    :code:`-no-properties` ::

            Don't include property information in the netlist output.


    ::

        The JSON schema for JNY output files is located in the "jny.schema.json" file
        which is located at "https://raw.githubusercontent.com/YosysHQ/yosys/master/misc/jny.schema.json"

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
        
