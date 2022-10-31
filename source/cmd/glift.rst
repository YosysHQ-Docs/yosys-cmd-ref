=====================================================
glift - create GLIFT models and optimization problems
=====================================================

.. raw:: latex

    \begin{comment}

:code:`yosys> help glift`
--------------------------------------------------------------------------------

.. container:: cmdref


    .. code:: yoscrypt

        glift <command> [options] [selection]

    ::

        Augments the current or specified module with gate-level information flow 
        tracking (GLIFT) logic using the "constructive mapping" approach. Also can set
        up QBF-SAT optimization problems in order to optimize GLIFT models or trade off
        precision and complexity.


        Commands:


    .. code:: yoscrypt

        -create-precise-model

    ::

          Replaces the current or specified module with one that has corresponding
          "taint" inputs, outputs, and internal nets along with precise taint
          tracking logic. For example, precise taint tracking logic for an AND gate
          is:

            y_t = a & b_t | b & a_t | a_t & b_t



    .. code:: yoscrypt

        -create-imprecise-model

    ::

          Replaces the current or specified module with one that has corresponding
          "taint" inputs, outputs, and internal nets along with imprecise "All OR"
          taint tracking logic:

            y_t = a_t | b_t



    .. code:: yoscrypt

        -create-instrumented-model

    ::

          Replaces the current or specified module with one that has corresponding
          "taint" inputs, outputs, and internal nets along with 4 varying-precision
          versions of taint tracking logic. Which version of taint tracking logic is
          used for a given gate is determined by a MUX selected by an $anyconst cell.
           By default, unless the `-no-cost-model` option is provided, an additional
          wire named `__glift_weight` with the `keep` and `minimize` attributes is
          added to the module along with pmuxes and adders to calculate a rough
          estimate of the number of logic gates in the GLIFT model given an assignment
          for the $anyconst cells. The four versions of taint tracking logic for an
          AND gate are:
            y_t = a & b_t | b & a_t | a_t & b_t       (like `-create-precise-model`)
            y_t = a_t | a & b_t
            y_t = b_t | b & a_t
            y_t = a_t | b_t                           (like `-create-imprecise-model`)



    ::

        Options:


    .. code:: yoscrypt

        -taint-constants

    ::

          Constant values in the design are labeled as tainted.
          (default: label constants as un-tainted)


    .. code:: yoscrypt

        -keep-outputs

    ::

          Do not remove module outputs. Taint tracking outputs will appear in the
          module ports alongside the orignal outputs.
          (default: original module outputs are removed)


    .. code:: yoscrypt

        -simple-cost-model

    ::

          Do not model logic area. Instead model the number of non-zero assignments to
          $anyconsts. Taint tracking logic versions vary in their size, but all
          reduced-precision versions are significantly smaller than the fully-precise
          version. A non-zero $anyconst assignment means that reduced-precision taint
          tracking logic was chosen for some gate. Only applicable in combination with
          `-create-instrumented-model`. (default: use a complex model and give that
           wire the "keep" and "minimize" attributes)


    .. code:: yoscrypt

        -no-cost-model

    ::

          Do not model taint tracking logic area and do not create a `__glift_weight`
          wire. Only applicable in combination with `-create-instrumented-model`.
          (default: model area and give that wire the "keep" and "minimize"
          attributes)


    .. code:: yoscrypt

        -instrument-more

    ::

          Allow choice from more versions of (even simpler) taint tracking logic. A
          total of 8 versions of taint tracking logic will be added per gate,
          including the 4 versions from `-create-instrumented-model` and these
          additional versions:

            y_t = a_t
            y_t = b_t
            y_t = 1
            y_t = 0

          Only applicable in combination with `-create-instrumented-model`.
          (default: do not add more versions of taint tracking logic.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            glift <command> [options] [selection]
        
        Augments the current or specified module with gate-level information flow 
        tracking (GLIFT) logic using the "constructive mapping" approach. Also can set
        up QBF-SAT optimization problems in order to optimize GLIFT models or trade off
        precision and complexity.
        
        
        Commands:
        
          -create-precise-model
            Replaces the current or specified module with one that has corresponding
            "taint" inputs, outputs, and internal nets along with precise taint
            tracking logic. For example, precise taint tracking logic for an AND gate
            is:
        
              y_t = a & b_t | b & a_t | a_t & b_t
        
        
          -create-imprecise-model
            Replaces the current or specified module with one that has corresponding
            "taint" inputs, outputs, and internal nets along with imprecise "All OR"
            taint tracking logic:
        
              y_t = a_t | b_t
        
        
          -create-instrumented-model
            Replaces the current or specified module with one that has corresponding
            "taint" inputs, outputs, and internal nets along with 4 varying-precision
            versions of taint tracking logic. Which version of taint tracking logic is
            used for a given gate is determined by a MUX selected by an $anyconst cell.
             By default, unless the `-no-cost-model` option is provided, an additional
            wire named `__glift_weight` with the `keep` and `minimize` attributes is
            added to the module along with pmuxes and adders to calculate a rough
            estimate of the number of logic gates in the GLIFT model given an assignment
            for the $anyconst cells. The four versions of taint tracking logic for an
            AND gate are:
              y_t = a & b_t | b & a_t | a_t & b_t       (like `-create-precise-model`)
              y_t = a_t | a & b_t
              y_t = b_t | b & a_t
              y_t = a_t | b_t                           (like `-create-imprecise-model`)
        
        
        Options:
        
          -taint-constants
            Constant values in the design are labeled as tainted.
            (default: label constants as un-tainted)
        
          -keep-outputs
            Do not remove module outputs. Taint tracking outputs will appear in the
            module ports alongside the orignal outputs.
            (default: original module outputs are removed)
        
          -simple-cost-model
            Do not model logic area. Instead model the number of non-zero assignments to
            $anyconsts. Taint tracking logic versions vary in their size, but all
            reduced-precision versions are significantly smaller than the fully-precise
            version. A non-zero $anyconst assignment means that reduced-precision taint
            tracking logic was chosen for some gate. Only applicable in combination with
            `-create-instrumented-model`. (default: use a complex model and give that
             wire the "keep" and "minimize" attributes)
        
          -no-cost-model
            Do not model taint tracking logic area and do not create a `__glift_weight`
            wire. Only applicable in combination with `-create-instrumented-model`.
            (default: model area and give that wire the "keep" and "minimize"
            attributes)
        
          -instrument-more
            Allow choice from more versions of (even simpler) taint tracking logic. A
            total of 8 versions of taint tracking logic will be added per gate,
            including the 4 versions from `-create-instrumented-model` and these
            additional versions:
        
              y_t = a_t
              y_t = b_t
              y_t = 1
              y_t = 0
        
            Only applicable in combination with `-create-instrumented-model`.
            (default: do not add more versions of taint tracking logic.
        
