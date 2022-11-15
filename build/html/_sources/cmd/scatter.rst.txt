==========================================
scatter - add additional intermediate nets
==========================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help scatter`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        scatter [selection]

    ::

        This command adds additional intermediate nets on all cell ports. This is used
        for testing the correct use of the SigMap helper in passes. If you don't know
        what this means: don't worry -- you only need this pass when testing your own
        extensions to Yosys.

        Use the opt_clean command to get rid of the additional nets.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            scatter [selection]
        
        This command adds additional intermediate nets on all cell ports. This is used
        for testing the correct use of the SigMap helper in passes. If you don't know
        what this means: don't worry -- you only need this pass when testing your own
        extensions to Yosys.
        
        Use the opt_clean command to get rid of the additional nets.
        
