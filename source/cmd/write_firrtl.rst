============================================
write_firrtl - write design to a FIRRTL file
============================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_firrtl`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_firrtl [options] [filename]

    ::

        Write a FIRRTL netlist of the current design.
        The following commands are executed by this command:
                pmuxtree
                bmuxmap
                demuxmap
                bwmuxmap

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_firrtl [options] [filename]
        
        Write a FIRRTL netlist of the current design.
        The following commands are executed by this command:
                pmuxtree
                bmuxmap
                demuxmap
                bwmuxmap
        
