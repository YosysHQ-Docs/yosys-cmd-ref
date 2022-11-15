==========================================================
write_intersynth - write design to InterSynth netlist file
==========================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_intersynth`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_intersynth [options] [filename]

    ::

        Write the current design to an 'intersynth' netlist file. InterSynth is
        a tool for Coarse-Grain Example-Driven Interconnect Synthesis.


    .. code:: yoscrypt

        -notypes

    ::

            do not generate celltypes and conntypes commands. i.e. just output
            the netlists. this is used for postsilicon synthesis.


    .. code:: yoscrypt

        -lib <verilog_or_rtlil_file>

    ::

            Use the specified library file for determining whether cell ports are
            inputs or outputs. This option can be used multiple times to specify
            more than one library.


    .. code:: yoscrypt

        -selected

    ::

            only write selected modules. modules must be selected entirely or
            not at all.


    ::

        http://bygone.clairexen.net/intersynth/

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_intersynth [options] [filename]
        
        Write the current design to an 'intersynth' netlist file. InterSynth is
        a tool for Coarse-Grain Example-Driven Interconnect Synthesis.
        
            -notypes
                do not generate celltypes and conntypes commands. i.e. just output
                the netlists. this is used for postsilicon synthesis.
        
            -lib <verilog_or_rtlil_file>
                Use the specified library file for determining whether cell ports are
                inputs or outputs. This option can be used multiple times to specify
                more than one library.
        
            -selected
                only write selected modules. modules must be selected entirely or
                not at all.
        
        http://bygone.clairexen.net/intersynth/
        
