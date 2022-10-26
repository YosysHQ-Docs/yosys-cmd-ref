=======================
read - load HDL designs
=======================

.. only:: html

    :code:`yosys> help read`
    ----------------------------------------------------------------------------


    :code:`read {-vlog95|-vlog2k|-sv2005|-sv2009|-sv2012|-sv|-formal} <verilog-file>..` ::

        Load the specified Verilog/SystemVerilog files. (Full SystemVerilog support
        is only available via Verific.)

        Additional -D<macro>[=<value>] options may be added after the option indicating
        the language version (and before file names) to set additional verilog defines.



    :code:`read {-vhdl87|-vhdl93|-vhdl2k|-vhdl2008|-vhdl} <vhdl-file>..` ::

        Load the specified VHDL files. (Requires Verific.)



    :code:`read {-f|-F} <command-file>` ::

        Load and execute the specified command file. (Requires Verific.)
        Check verific command for more information about supported commands in file.



    :code:`read -define <macro>[=<value>]..` ::

        Set global Verilog/SystemVerilog defines.



    :code:`read -undef <macro>..` ::

        Unset global Verilog/SystemVerilog defines.



    :code:`read -incdir <directory>` ::

        Add directory to global Verilog/SystemVerilog include directories.



    :code:`read -verific`

    :code:`read -noverific` ::

        Subsequent calls to 'read' will either use or not use Verific. Calling 'read'
        with -verific will result in an error on Yosys binaries that are built without
        Verific support. The default is to use Verific if it is available.

.. only:: latex

    ::

        
            read {-vlog95|-vlog2k|-sv2005|-sv2009|-sv2012|-sv|-formal} <verilog-file>..
        
        Load the specified Verilog/SystemVerilog files. (Full SystemVerilog support
        is only available via Verific.)
        
        Additional -D<macro>[=<value>] options may be added after the option indicating
        the language version (and before file names) to set additional verilog defines.
        
        
            read {-vhdl87|-vhdl93|-vhdl2k|-vhdl2008|-vhdl} <vhdl-file>..
        
        Load the specified VHDL files. (Requires Verific.)
        
        
            read {-f|-F} <command-file>
        
        Load and execute the specified command file. (Requires Verific.)
        Check verific command for more information about supported commands in file.
        
        
            read -define <macro>[=<value>]..
        
        Set global Verilog/SystemVerilog defines.
        
        
            read -undef <macro>..
        
        Unset global Verilog/SystemVerilog defines.
        
        
            read -incdir <directory>
        
        Add directory to global Verilog/SystemVerilog include directories.
        
        
            read -verific
            read -noverific
        
        Subsequent calls to 'read' will either use or not use Verific. Calling 'read'
        with -verific will result in an error on Yosys binaries that are built without
        Verific support. The default is to use Verific if it is available.
        
