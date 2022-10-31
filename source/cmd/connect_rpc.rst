=====================================
connect_rpc - connect to RPC frontend
=====================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help connect_rpc`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        connect_rpc -exec <command> [args...]

   
    .. code:: yoscrypt

        connect_rpc -path <path>

    ::

        Load modules using an out-of-process frontend.


    .. code:: yoscrypt

        -exec <command> [args...]

    ::

            run <command> with arguments [args...]. send requests on stdin, read
            responses from stdout.


    .. code:: yoscrypt

        -path <path>

    ::

            connect to Unix domain socket at <path>. (Unix)
            connect to bidirectional byte-type named pipe at <path>. (Windows)


    ::

        A simple JSON-based, newline-delimited protocol is used for communicating with
        the frontend. Yosys requests data from the frontend by sending exactly 1 line
        of JSON. Frontend responds with data or error message by replying with exactly
        1 line of JSON as well.

            -> {"method": "modules"}
            <- {"modules": ["<module-name>", ...]}
            <- {"error": "<error-message>"}
                request for the list of modules that can be derived by this frontend.
                the 'hierarchy' command will call back into this frontend if a cell
                with type <module-name> is instantiated in the design.

            -> {"method": "derive", "module": "<module-name">, "parameters": {
                "<param-name>": {"type": "[unsigned|signed|string|real]",
                                   "value": "<param-value>"}, ...}}
            <- {"frontend": "[rtlil|verilog|...]","source": "<source>"}}
            <- {"error": "<error-message>"}
                request for the module <module-name> to be derived for a specific set of
                parameters. <param-name> starts with \ for named parameters, and with $
                for unnamed parameters, which are numbered starting at 1.<param-value>
                for integer parameters is always specified as a binary string of
                unlimited precision. the <source> returned by the frontend is
                hygienically parsedby a built-in Yosys <frontend>, allowing the RPC
                frontend to return anyconvenient representation of the module. the
                derived module is cached,so the response should be the same whenever the
                same set of parameters is provided.
.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            connect_rpc -exec <command> [args...]
            connect_rpc -path <path>
        
        Load modules using an out-of-process frontend.
        
            -exec <command> [args...]
                run <command> with arguments [args...]. send requests on stdin, read
                responses from stdout.
        
            -path <path>
                connect to Unix domain socket at <path>. (Unix)
                connect to bidirectional byte-type named pipe at <path>. (Windows)
        
        A simple JSON-based, newline-delimited protocol is used for communicating with
        the frontend. Yosys requests data from the frontend by sending exactly 1 line
        of JSON. Frontend responds with data or error message by replying with exactly
        1 line of JSON as well.
        
            -> {"method": "modules"}
            <- {"modules": ["<module-name>", ...]}
            <- {"error": "<error-message>"}
                request for the list of modules that can be derived by this frontend.
                the 'hierarchy' command will call back into this frontend if a cell
                with type <module-name> is instantiated in the design.
        
            -> {"method": "derive", "module": "<module-name">, "parameters": {
                "<param-name>": {"type": "[unsigned|signed|string|real]",
                                   "value": "<param-value>"}, ...}}
            <- {"frontend": "[rtlil|verilog|...]","source": "<source>"}}
            <- {"error": "<error-message>"}
                request for the module <module-name> to be derived for a specific set of
                parameters. <param-name> starts with \ for named parameters, and with $
                for unnamed parameters, which are numbered starting at 1.<param-value>
                for integer parameters is always specified as a binary string of
                unlimited precision. the <source> returned by the frontend is
                hygienically parsedby a built-in Yosys <frontend>, allowing the RPC
                frontend to return anyconvenient representation of the module. the
                derived module is cached,so the response should be the same whenever the
                same set of parameters is provided.
