======================================
connect - create or remove connections
======================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help connect`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        connect [-nomap] [-nounset] -set <lhs-expr> <rhs-expr> [selection]

    ::

        Create a connection. This is equivalent to adding the statement 'assign
        <lhs-expr> = <rhs-expr>;' to the Verilog input. Per default, all existing
        drivers for <lhs-expr> are unconnected. This can be overwritten by using
        the -nounset option.


    .. code:: yoscrypt

        connect [-nomap] -unset <expr> [selection]

    ::

        Unconnect all existing drivers for the specified expression.


    .. code:: yoscrypt

        connect [-nomap] [-assert] -port <cell> <port> <expr> [selection]

    ::

        Connect the specified cell port to the specified cell port.


        Per default signal alias names are resolved and all signal names are mapped
        the the signal name of the primary driver. Using the -nomap option deactivates
        this behavior.

        The connect command operates in one module only. Either only one module must
        be selected or an active module must be set using the 'cd' command.

        The -assert option verifies that the connection already exists, instead of
        making it.

        This command does not operate on module with processes.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            connect [-nomap] [-nounset] -set <lhs-expr> <rhs-expr> [selection]
        
        Create a connection. This is equivalent to adding the statement 'assign
        <lhs-expr> = <rhs-expr>;' to the Verilog input. Per default, all existing
        drivers for <lhs-expr> are unconnected. This can be overwritten by using
        the -nounset option.
        
        
            connect [-nomap] -unset <expr> [selection]
        
        Unconnect all existing drivers for the specified expression.
        
        
            connect [-nomap] [-assert] -port <cell> <port> <expr> [selection]
        
        Connect the specified cell port to the specified cell port.
        
        
        Per default signal alias names are resolved and all signal names are mapped
        the the signal name of the primary driver. Using the -nomap option deactivates
        this behavior.
        
        The connect command operates in one module only. Either only one module must
        be selected or an active module must be set using the 'cd' command.
        
        The -assert option verifies that the connection already exists, instead of
        making it.
        
        This command does not operate on module with processes.
        
