=====================================================
verilog_defines - define and undefine verilog defines
=====================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: verilog_defines
    :title: define and undefine verilog defines



    .. code:: yoscrypt

        verilog_defines [options]

    ::

        Define and undefine verilog preprocessor macros.


    .. code:: yoscrypt

        -Dname[=definition]

    ::

            define the preprocessor symbol 'name' and set its optional value
            'definition'


    .. code:: yoscrypt

        -Uname[=definition]

    ::

            undefine the preprocessor symbol 'name'


    .. code:: yoscrypt

        -reset

    ::

            clear list of defined preprocessor symbols


    .. code:: yoscrypt

        -list

    ::

            list currently defined preprocessor symbols

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            verilog_defines [options]
        
        Define and undefine verilog preprocessor macros.
        
            -Dname[=definition]
                define the preprocessor symbol 'name' and set its optional value
                'definition'
        
            -Uname[=definition]
                undefine the preprocessor symbol 'name'
        
            -reset
                clear list of defined preprocessor symbols
        
            -list
                list currently defined preprocessor symbols
        
