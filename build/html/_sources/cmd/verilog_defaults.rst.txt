=======================================================
verilog_defaults - set default options for read_verilog
=======================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help verilog_defaults`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        verilog_defaults -add [options]

    ::

        Add the specified options to the list of default options to read_verilog.


    .. code:: yoscrypt

        verilog_defaults -clear

    ::

        Clear the list of Verilog default options.


    .. code:: yoscrypt

        verilog_defaults -push

   
    .. code:: yoscrypt

        verilog_defaults -pop

    ::

        Push or pop the list of default options to a stack. Note that -push does
        not imply -clear.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            verilog_defaults -add [options]
        
        Add the specified options to the list of default options to read_verilog.
        
        
            verilog_defaults -clear
        
        Clear the list of Verilog default options.
        
        
            verilog_defaults -push
            verilog_defaults -pop
        
        Push or pop the list of default options to a stack. Note that -push does
        not imply -clear.
        
