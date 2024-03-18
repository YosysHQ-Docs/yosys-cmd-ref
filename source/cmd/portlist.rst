=================================
portlist - list (top-level) ports
=================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: portlist
    :title: list (top-level) ports



    .. code:: yoscrypt

        portlist [options] [selection]

    ::

        This command lists all module ports found in the selected modules.

        If no selection is provided then it lists the ports on the top module.


    .. code:: yoscrypt

        -m

    ::

          print verilog blackbox module definitions instead of port lists

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            portlist [options] [selection]
        
        This command lists all module ports found in the selected modules.
        
        If no selection is provided then it lists the ports on the top module.
        
          -m
            print verilog blackbox module definitions instead of port lists
        
