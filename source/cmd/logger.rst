==============================
logger - set logger properties
==============================

.. only:: html

    :code:`yosys> help logger`
    ----------------------------------------------------------------------------


    :code:`logger [options]` ::

        This command sets global logger properties, also available using command line
        options.


    :code:`-[no]time` ::

            enable/disable display of timestamp in log output.


    :code:`-[no]stderr` ::

            enable/disable logging errors to stderr.


    :code:`-warn regex` ::

            print a warning for all log messages matching the regex.


    :code:`-nowarn regex` ::

            if a warning message matches the regex, it is printed as regular
            message instead.


    :code:`-werror regex` ::

            if a warning message matches the regex, it is printed as error
            message instead and the tool terminates with a nonzero return code.


    :code:`-[no]debug` ::

            globally enable/disable debug log messages.


    :code:`-experimental <feature>` ::

            do not print warnings for the specified experimental feature


    :code:`-expect <type> <regex> <expected_count>` ::

            expect log, warning or error to appear. matched errors will terminate
            with exit code 0.


    :code:`-expect-no-warnings` ::

            gives error in case there is at least one warning that is not expected.


    :code:`-check-expected` ::

            verifies that the patterns previously set up by -expect have actually
            been met, then clears the expected log list.  If this is not called
            manually, the check will happen at yosys exist time instead.

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
        
