=======================================================
verilog_defaults - set default options for read_verilog
=======================================================

.. only:: html

    :code:`yosys> help verilog_defaults`
    ----------------------------------------------------------------------------


    :code:`verilog_defaults -add [options]` ::

        Add the specified options to the list of default options to read_verilog.



    :code:`verilog_defaults -clear` ::

        Clear the list of Verilog default options.



    :code:`verilog_defaults -push`

    :code:`verilog_defaults -pop` ::

        Push or pop the list of default options to a stack. Note that -push does
        not imply -clear.

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
        
