=================================
qwp - quadratic wirelength placer
=================================

.. only:: html

    :code:`yosys> help qwp`
    ----------------------------------------------------------------------------


    :code:`qwp [options] [selection]` ::

        This command runs quadratic wirelength placement on the selected modules and
        annotates the cells in the design with 'qwp_position' attributes.


    :code:`-ltr` ::

            Add left-to-right constraints: constrain all inputs on the left border
            outputs to the right border.


    :code:`-alpha` ::

            Add constraints for inputs/outputs to be placed in alphanumerical
            order along the y-axis (top-to-bottom).


    :code:`-grid N` ::

            Number of grid divisions in x- and y-direction. (default=16)


    :code:`-dump <html_file_name>` ::

            Dump a protocol of the placement algorithm to the html file.


    :code:`-v` ::

            Verbose solver output for profiling or debugging


    ::

        Note: This implementation of a quadratic wirelength placer uses exact
        dense matrix operations. It is only a toy-placer for small circuits.

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
        
