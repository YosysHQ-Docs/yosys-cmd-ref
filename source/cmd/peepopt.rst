===========================================
peepopt - collection of peephole optimizers
===========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: peepopt
    :title: collection of peephole optimizers



    .. code:: yoscrypt

        peepopt [options] [selection]

    ::

        This pass applies a collection of peephole optimizers to the current design.

        This pass employs the following rules:

           * muldiv - Replace (A*B)/B with A

           * shiftmul - Replace A>>(B*C) with A'>>(B<<K) where C and K are constants
                        and A' is derived from A by appropriately inserting padding
                        into the signal. (right variant)

                        Analogously, replace A<<(B*C) with appropriate selection of
                        output bits from A<<(B<<K). (left variant)

           * shiftadd - Replace A>>(B+D) with (A'>>D)>>(B) where D is constant and
                        A' is derived from A by padding or cutting inaccessible bits.
                        Scratchpad: 'peepopt.shiftadd.max_data_multiple' (default: 2)
                        limits the amount of padding to a multiple of the data, 
                        to avoid high resource usage from large temporary MUX trees.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            peepopt [options] [selection]
        
        This pass applies a collection of peephole optimizers to the current design.
        
        This pass employs the following rules:
        
           * muldiv - Replace (A*B)/B with A
        
           * shiftmul - Replace A>>(B*C) with A'>>(B<<K) where C and K are constants
                        and A' is derived from A by appropriately inserting padding
                        into the signal. (right variant)
        
                        Analogously, replace A<<(B*C) with appropriate selection of
                        output bits from A<<(B<<K). (left variant)
        
           * shiftadd - Replace A>>(B+D) with (A'>>D)>>(B) where D is constant and
                        A' is derived from A by padding or cutting inaccessible bits.
                        Scratchpad: 'peepopt.shiftadd.max_data_multiple' (default: 2)
                        limits the amount of padding to a multiple of the data, 
                        to avoid high resource usage from large temporary MUX trees.
        
