=================================
qwp - quadratic wirelength placer
=================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help qwp`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        qwp [options] [selection]

    ::

        This command runs quadratic wirelength placement on the selected modules and
        annotates the cells in the design with 'qwp_position' attributes.


    .. code:: yoscrypt

        -ltr

    ::

            Add left-to-right constraints: constrain all inputs on the left border
            outputs to the right border.


    .. code:: yoscrypt

        -alpha

    ::

            Add constraints for inputs/outputs to be placed in alphanumerical
            order along the y-axis (top-to-bottom).


    .. code:: yoscrypt

        -grid N

    ::

            Number of grid divisions in x- and y-direction. (default=16)


    .. code:: yoscrypt

        -dump <html_file_name>

    ::

            Dump a protocol of the placement algorithm to the html file.


    .. code:: yoscrypt

        -v

    ::

            Verbose solver output for profiling or debugging


    ::

        Note: This implementation of a quadratic wirelength placer uses exact
        dense matrix operations. It is only a toy-placer for small circuits.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            qwp [options] [selection]
        
        This command runs quadratic wirelength placement on the selected modules and
        annotates the cells in the design with 'qwp_position' attributes.
        
            -ltr
                Add left-to-right constraints: constrain all inputs on the left border
                outputs to the right border.
        
            -alpha
                Add constraints for inputs/outputs to be placed in alphanumerical
                order along the y-axis (top-to-bottom).
        
            -grid N
                Number of grid divisions in x- and y-direction. (default=16)
        
            -dump <html_file_name>
                Dump a protocol of the placement algorithm to the html file.
        
            -v
                Verbose solver output for profiling or debugging
        
        Note: This implementation of a quadratic wirelength placer uses exact
        dense matrix operations. It is only a toy-placer for small circuits.
        
