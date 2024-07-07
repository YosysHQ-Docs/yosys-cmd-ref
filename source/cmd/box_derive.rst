===============================
box_derive - derive box modules
===============================

.. raw:: latex

    \begin{comment}

.. cmd:def:: box_derive
    :title: derive box modules



    .. code:: yoscrypt

        box_derive [-base <base_module>] [-naming_attr <attr>] [selection]

    ::

        As part of the assembly of the design hierarchy done by the 'hierarchy' command,
        specializations of parametric modules are derived on demand: for each choice of
        parameter values appearing in the design, a copy of the parametric module is
        derived which is specialized to that choice.

        This derivation process ignores blackboxes and whiteboxes (boxes). To supplement,
        this 'box_derive' command can be used to request the derivation of modules based
        on box instances appearing in the design, which is desirable in certain use
        cases. Only the selected cells are considered as the instances that steer the
        derivation process.


    .. code:: yoscrypt

        -base <base_module>

    ::

            instead of deriving the module that directly corresponds to each box
            instance, derive a specialization of <base_module> (this option applies
            to all selected box cells)


    .. code:: yoscrypt

        -naming_attr <attr>

    ::

            once a specialization is derived, use the value of the module attribute
            <attr> for a name which should be used for the derived module (this
            replaces the internal Yosys naming scheme in which the names of derived
            modules start with '$paramod$')

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            box_derive [-base <base_module>] [-naming_attr <attr>] [selection]
        
        As part of the assembly of the design hierarchy done by the 'hierarchy' command,
        specializations of parametric modules are derived on demand: for each choice of
        parameter values appearing in the design, a copy of the parametric module is
        derived which is specialized to that choice.
        
        This derivation process ignores blackboxes and whiteboxes (boxes). To supplement,
        this 'box_derive' command can be used to request the derivation of modules based
        on box instances appearing in the design, which is desirable in certain use
        cases. Only the selected cells are considered as the instances that steer the
        derivation process.
        
            -base <base_module>
                instead of deriving the module that directly corresponds to each box
                instance, derive a specialization of <base_module> (this option applies
                to all selected box cells)
        
            -naming_attr <attr>
                once a specialization is derived, use the value of the module attribute
                <attr> for a name which should be used for the derived module (this
                replaces the internal Yosys naming scheme in which the names of derived
                modules start with '$paramod$')
        
