$_MUX16_
========

A 16-input MUX gate.
::

   Truth table:    A B C D E F G H I J K L M N O P S T U V | Y
                  -----------------------------------------+---
                   a - - - - - - - - - - - - - - - 0 0 0 0 | a
                   - b - - - - - - - - - - - - - - 1 0 0 0 | b
                   - - c - - - - - - - - - - - - - 0 1 0 0 | c
                   - - - d - - - - - - - - - - - - 1 1 0 0 | d
                   - - - - e - - - - - - - - - - - 0 0 1 0 | e
                   - - - - - f - - - - - - - - - - 1 0 1 0 | f
                   - - - - - - g - - - - - - - - - 0 1 1 0 | g
                   - - - - - - - h - - - - - - - - 1 1 1 0 | h
                   - - - - - - - - i - - - - - - - 0 0 0 1 | i
                   - - - - - - - - - j - - - - - - 1 0 0 1 | j
                   - - - - - - - - - - k - - - - - 0 1 0 1 | k
                   - - - - - - - - - - - l - - - - 1 1 0 1 | l
                   - - - - - - - - - - - - m - - - 0 0 1 1 | m
                   - - - - - - - - - - - - - n - - 1 0 1 1 | n
                   - - - - - - - - - - - - - - o - 0 1 1 1 | o
                   - - - - - - - - - - - - - - - p 1 1 1 1 | p
   
Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simcells.v:321

   module \$_MUX16_ (A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P, S, T, U, V, Y);
       input A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P, S, T, U, V;
       output Y;
       assign Y = V ? U ? T ? (S ? P : O) :
                              (S ? N : M) :
                          T ? (S ? L : K) :
                              (S ? J : I) :
                      U ? T ? (S ? H : G) :
                              (S ? F : E) :
                          T ? (S ? D : C) :
                              (S ? B : A);
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $_MUX16_``.
