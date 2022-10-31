==============================
shregmap - map shift registers
==============================

.. raw:: latex

    \begin{comment}

:code:`yosys> help shregmap`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        shregmap [options] [selection]

    ::

        This pass converts chains of $_DFF_[NP]_ gates to target specific shift register
        primitives. The generated shift register will be of type $__SHREG_DFF_[NP]_ and
        will use the same interface as the original $_DFF_*_ cells. The cell parameter
        'DEPTH' will contain the depth of the shift register. Use a target-specific
        'techmap' map file to convert those cells to the actual target cells.


    .. code:: yoscrypt

        -minlen N

    ::

            minimum length of shift register (default = 2)
            (this is the length after -keep_before and -keep_after)


    .. code:: yoscrypt

        -maxlen N

    ::

            maximum length of shift register (default = no limit)
            larger chains will be mapped to multiple shift register instances


    .. code:: yoscrypt

        -keep_before N

    ::

            number of DFFs to keep before the shift register (default = 0)


    .. code:: yoscrypt

        -keep_after N

    ::

            number of DFFs to keep after the shift register (default = 0)


    .. code:: yoscrypt

        -clkpol pos|neg|any

    ::

            limit match to only positive or negative edge clocks. (default = any)


    .. code:: yoscrypt

        -enpol pos|neg|none|any_or_none|any

    ::

            limit match to FFs with the specified enable polarity. (default = none)


    .. code:: yoscrypt

        -match <cell_type>[:<d_port_name>:<q_port_name>]

    ::

            match the specified cells instead of $_DFF_N_ and $_DFF_P_. If
            ':<d_port_name>:<q_port_name>' is omitted then 'D' and 'Q' is used
            by default. E.g. the option '-clkpol pos' is just an alias for
            '-match $_DFF_P_', which is an alias for '-match $_DFF_P_:D:Q'.


    .. code:: yoscrypt

        -params

    ::

            instead of encoding the clock and enable polarity in the cell name by
            deriving from the original cell name, simply name all generated cells
            $__SHREG_ and use CLKPOL and ENPOL parameters. An ENPOL value of 2 is
            used to denote cells without enable input. The ENPOL parameter is
            omitted when '-enpol none' (or no -enpol option) is passed.


    .. code:: yoscrypt

        -zinit

    ::

            assume the shift register is automatically zero-initialized, so it
            becomes legal to merge zero initialized FFs into the shift register.


    .. code:: yoscrypt

        -init

    ::

            map initialized registers to the shift reg, add an INIT parameter to
            generated cells with the initialization value. (first bit to shift out
            in LSB position)


    .. code:: yoscrypt

        -tech greenpak4

    ::

            map to greenpak4 shift registers.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            shregmap [options] [selection]
        
        This pass converts chains of $_DFF_[NP]_ gates to target specific shift register
        primitives. The generated shift register will be of type $__SHREG_DFF_[NP]_ and
        will use the same interface as the original $_DFF_*_ cells. The cell parameter
        'DEPTH' will contain the depth of the shift register. Use a target-specific
        'techmap' map file to convert those cells to the actual target cells.
        
            -minlen N
                minimum length of shift register (default = 2)
                (this is the length after -keep_before and -keep_after)
        
            -maxlen N
                maximum length of shift register (default = no limit)
                larger chains will be mapped to multiple shift register instances
        
            -keep_before N
                number of DFFs to keep before the shift register (default = 0)
        
            -keep_after N
                number of DFFs to keep after the shift register (default = 0)
        
            -clkpol pos|neg|any
                limit match to only positive or negative edge clocks. (default = any)
        
            -enpol pos|neg|none|any_or_none|any
                limit match to FFs with the specified enable polarity. (default = none)
        
            -match <cell_type>[:<d_port_name>:<q_port_name>]
                match the specified cells instead of $_DFF_N_ and $_DFF_P_. If
                ':<d_port_name>:<q_port_name>' is omitted then 'D' and 'Q' is used
                by default. E.g. the option '-clkpol pos' is just an alias for
                '-match $_DFF_P_', which is an alias for '-match $_DFF_P_:D:Q'.
        
            -params
                instead of encoding the clock and enable polarity in the cell name by
                deriving from the original cell name, simply name all generated cells
                $__SHREG_ and use CLKPOL and ENPOL parameters. An ENPOL value of 2 is
                used to denote cells without enable input. The ENPOL parameter is
                omitted when '-enpol none' (or no -enpol option) is passed.
        
            -zinit
                assume the shift register is automatically zero-initialized, so it
                becomes legal to merge zero initialized FFs into the shift register.
        
            -init
                map initialized registers to the shift reg, add an INIT parameter to
                generated cells with the initialization value. (first bit to shift out
                in LSB position)
        
            -tech greenpak4
                map to greenpak4 shift registers.
        
