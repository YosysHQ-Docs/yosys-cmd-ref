===================================
write_file - write a text to a file
===================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help write_file`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        write_file [options] output_file [input_file]

    ::

        Write the text from the input file to the output file.


    .. code:: yoscrypt

        -a

    ::

            Append to output file (instead of overwriting)



    ::

        Inside a script the input file can also can a here-document:

            write_file hello.txt <<EOT
            Hello World!
            EOT

.. raw:: latex

    \end{comment}

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
        
