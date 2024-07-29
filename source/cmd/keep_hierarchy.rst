=================================================
keep_hierarchy - add the keep_hierarchy attribute
=================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: keep_hierarchy
    :title: add the keep_hierarchy attribute



    .. code:: yoscrypt

        keep_hierarchy [options]

    ::

        Add the keep_hierarchy attribute.


    .. code:: yoscrypt

        -min_cost <min_cost>

    ::

            only add the attribute to modules estimated to have more
            than <min_cost> gates after simple techmapping. Intended
            for tuning trade-offs between quality and yosys runtime.
.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            keep_hierarchy [options]
        
        Add the keep_hierarchy attribute.
        
            -min_cost <min_cost>
                only add the attribute to modules estimated to have more
                than <min_cost> gates after simple techmapping. Intended
                for tuning trade-offs between quality and yosys runtime.
