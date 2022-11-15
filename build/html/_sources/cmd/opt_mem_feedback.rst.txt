====================================================================================
opt_mem_feedback - convert memory read-to-write port feedback paths to write enables
====================================================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help opt_mem_feedback`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        opt_mem_feedback [selection]

    ::

        This pass detects cases where an asynchronous read port is only connected via
        a mux tree to a write port with the same address.  When such a connection is
        found, it is replaced with a new condition on an enable signal, allowing
        for removal of the read port.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            opt_mem_feedback [selection]
        
        This pass detects cases where an asynchronous read port is only connected via
        a mux tree to a write port with the same address.  When such a connection is
        found, it is replaced with a new condition on an enable signal, allowing
        for removal of the read port.
        
