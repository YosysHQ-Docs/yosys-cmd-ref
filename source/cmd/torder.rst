=========================================
torder - print cells in topological order
=========================================

.. only:: html

    :code:`yosys> help torder`
    ----------------------------------------------------------------------------


    :code:`torder [options] [selection]` ::

        This command prints the selected cells in topological order.


    :code:`-stop <cell_type> <cell_port>` ::

            do not use the specified cell port in topological sorting


    :code:`-noautostop` ::

            by default Q outputs of internal FF cells and memory read port outputs
            are not used in topological sorting. this option deactivates that.

.. only:: latex

    ::

        
            torder [options] [selection]
        
        This command prints the selected cells in topological order.
        
            -stop <cell_type> <cell_port>
                do not use the specified cell port in topological sorting
        
            -noautostop
                by default Q outputs of internal FF cells and memory read port outputs
                are not used in topological sorting. this option deactivates that.
        
