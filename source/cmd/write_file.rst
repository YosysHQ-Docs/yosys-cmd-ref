===================================
write_file - write a text to a file
===================================

.. only:: html

    :code:`yosys> help write_file`
    ----------------------------------------------------------------------------


    :code:`write_file [options] output_file [input_file]` ::

        Write the text from the input file to the output file.


    :code:`-a` ::

            Append to output file (instead of overwriting)



    ::

        Inside a script the input file can also can a here-document:

            write_file hello.txt <<EOT
            Hello World!
            EOT

.. only:: latex

    ::

        
            write_file [options] output_file [input_file]
        
        Write the text from the input file to the output file.
        
            -a
                Append to output file (instead of overwriting)
        
        
        Inside a script the input file can also can a here-document:
        
            write_file hello.txt <<EOT
            Hello World!
            EOT
        
