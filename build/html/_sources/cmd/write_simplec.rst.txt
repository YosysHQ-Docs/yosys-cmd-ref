===============================================
write_simplec - convert design to simple C code
===============================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_simplec`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_simplec [options] [filename]

    ::

        Write simple C code for simulating the design. The C code written can be used to
        simulate the design in a C environment, but the purpose of this command is to
        generate code that works well with C-based formal verification.


    .. code:: yoscrypt

        -verbose

    ::

            this will print the recursive walk used to export the modules.


    .. code:: yoscrypt

        -i8, -i16, -i32, -i64

    ::

            set the maximum integer bit width to use in the generated code.


    ::

        THIS COMMAND IS UNDER CONSTRUCTION

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_simplec [options] [filename]
        
        Write simple C code for simulating the design. The C code written can be used to
        simulate the design in a C environment, but the purpose of this command is to
        generate code that works well with C-based formal verification.
        
            -verbose
                this will print the recursive walk used to export the modules.
        
            -i8, -i16, -i32, -i64
                set the maximum integer bit width to use in the generated code.
        
        THIS COMMAND IS UNDER CONSTRUCTION
        
