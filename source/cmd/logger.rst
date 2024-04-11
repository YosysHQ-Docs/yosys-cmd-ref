==============================
logger - set logger properties
==============================

.. raw:: latex

    \begin{comment}

.. cmd:def:: logger
    :title: set logger properties



    .. code:: yoscrypt

        logger [options]

    ::

        This command sets global logger properties, also available using command line
        options.


    .. code:: yoscrypt

        -[no]time

    ::

            enable/disable display of timestamp in log output.


    .. code:: yoscrypt

        -[no]stderr

    ::

            enable/disable logging errors to stderr.


    .. code:: yoscrypt

        -warn regex

    ::

            print a warning for all log messages matching the regex.


    .. code:: yoscrypt

        -nowarn regex

    ::

            if a warning message matches the regex, it is printed as regular
            message instead.


    .. code:: yoscrypt

        -werror regex

    ::

            if a warning message matches the regex, it is printed as error
            message instead and the tool terminates with a nonzero return code.


    .. code:: yoscrypt

        -[no]debug

    ::

            globally enable/disable debug log messages.


    .. code:: yoscrypt

        -experimental <feature>

    ::

            do not print warnings for the specified experimental feature


    .. code:: yoscrypt

        -expect <type> <regex> <expected_count>

    ::

            expect log, warning or error to appear. matched errors will terminate
            with exit code 0.


    .. code:: yoscrypt

        -expect-no-warnings

    ::

            gives error in case there is at least one warning that is not expected.


    .. code:: yoscrypt

        -check-expected

    ::

            verifies that the patterns previously set up by -expect have actually
            been met, then clears the expected log list.  If this is not called
            manually, the check will happen at yosys exist time instead.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            logger [options]
        
        This command sets global logger properties, also available using command line
        options.
        
            -[no]time
                enable/disable display of timestamp in log output.
        
            -[no]stderr
                enable/disable logging errors to stderr.
        
            -warn regex
                print a warning for all log messages matching the regex.
        
            -nowarn regex
                if a warning message matches the regex, it is printed as regular
                message instead.
        
            -werror regex
                if a warning message matches the regex, it is printed as error
                message instead and the tool terminates with a nonzero return code.
        
            -[no]debug
                globally enable/disable debug log messages.
        
            -experimental <feature>
                do not print warnings for the specified experimental feature
        
            -expect <type> <regex> <expected_count>
                expect log, warning or error to appear. matched errors will terminate
                with exit code 0.
        
            -expect-no-warnings
                gives error in case there is at least one warning that is not expected.
        
            -check-expected
                verifies that the patterns previously set up by -expect have actually
                been met, then clears the expected log list.  If this is not called
                manually, the check will happen at yosys exist time instead.
        
