$macc
=====

.. cell:def:: $macc
   :title: $macc

   
       $macc (A, B, Y)
   
   Multiply and accumulate.
   A building block for summing any number of negated and unnegated signals
   and arithmetic products of pairs of signals. Cell port A concatenates pairs
   of signals to be multiplied together. When the second signal in a pair is zero
   length, a constant 1 is used instead as the second factor. Cell port B
   concatenates 1-bit-wide signals to also be summed, such as "carry in" in adders.
   Typically created by the `alumacc` pass, which transforms $add and $mul
   into $macc cells.

Properties
----------

- is_synthesizable: false
- is_combinatorial: false
- is_evaluable: true

Simulation model (Verilog)
--------------------------

.. code-block:: verilog
   :caption: simlib.v:914

   module \$macc (A, B, Y);
       
       parameter A_WIDTH = 0;
       parameter B_WIDTH = 0;
       parameter Y_WIDTH = 0;
       // CONFIG determines the layout of A, as explained below
       parameter CONFIG = 4'b0000;
       parameter CONFIG_WIDTH = 4;
       
       // In the terms used for this cell, there's mixed meanings for the term "port". To disambiguate:
       // A cell port is for example the A input (it is constructed in C++ as cell->setPort(ID::A, ...))
       // Multiplier ports are pairs of multiplier inputs ("factors").
       // If the second signal in such a pair is zero length, no multiplication is necessary, and the first signal is just added to the sum.
       input [A_WIDTH-1:0] A; // Cell port A is the concatenation of all arithmetic ports
       input [B_WIDTH-1:0] B; // Cell port B is the concatenation of single-bit unsigned signals to be also added to the sum
       output reg [Y_WIDTH-1:0] Y; // Output sum
       
       // Xilinx XSIM does not like $clog2() below..
       function integer my_clog2;
           input integer v;
           begin
               if (v > 0)
                   v = v - 1;
               my_clog2 = 0;
               while (v) begin
                   v = v >> 1;
                   my_clog2 = my_clog2 + 1;
               end
           end
       endfunction
       
       // Bits that a factor's length field in CONFIG per factor in cell port A
       localparam integer num_bits = CONFIG[3:0] > 0 ? CONFIG[3:0] : 1;
       // Number of multiplier ports
       localparam integer num_ports = (CONFIG_WIDTH-4) / (2 + 2*num_bits);
       // Minium bit width of an induction variable to iterate over all bits of cell port A
       localparam integer num_abits = my_clog2(A_WIDTH) > 0 ? my_clog2(A_WIDTH) : 1;
       
       // In this pseudocode, u(foo) means an unsigned int that's foo bits long.
       // The CONFIG parameter carries the following information:
       //    struct CONFIG {
       //        u4 num_bits;
       //        struct port_field {
       //            bool is_signed;
       //            bool is_subtract;
       //            u(num_bits) factor1_len;
       //            u(num_bits) factor2_len;
       //        }[num_ports];
       //    };
       
       // The A cell port carries the following information:
       //    struct A {
       //        u(CONFIG.port_field[0].factor1_len) port0factor1;
       //        u(CONFIG.port_field[0].factor2_len) port0factor2;
       //        u(CONFIG.port_field[1].factor1_len) port1factor1;
       //        u(CONFIG.port_field[1].factor2_len) port1factor2;
       //        ...
       //    };
       // and log(sizeof(A)) is num_abits.
       // No factor1 may have a zero length.
       // A factor2 having a zero length implies factor2 is replaced with a constant 1.
       
       // Additionally, B is an array of 1-bit-wide unsigned integers to also be summed up.
       // Finally, we have:
       // Y = port0factor1 * port0factor2 + port1factor1 * port1factor2 + ...
       //     * B[0] + B[1] + ...
       
       function [2*num_ports*num_abits-1:0] get_port_offsets;
           input [CONFIG_WIDTH-1:0] cfg;
           integer i, cursor;
           begin
               cursor = 0;
               get_port_offsets = 0;
               for (i = 0; i < num_ports; i = i+1) begin
                   get_port_offsets[(2*i + 0)*num_abits +: num_abits] = cursor;
                   cursor = cursor + cfg[4 + i*(2 + 2*num_bits) + 2 +: num_bits];
                   get_port_offsets[(2*i + 1)*num_abits +: num_abits] = cursor;
                   cursor = cursor + cfg[4 + i*(2 + 2*num_bits) + 2 + num_bits +: num_bits];
               end
           end
       endfunction
       
       localparam [2*num_ports*num_abits-1:0] port_offsets = get_port_offsets(CONFIG);
       
       `define PORT_IS_SIGNED   (0 + CONFIG[4 + i*(2 + 2*num_bits)])
       `define PORT_DO_SUBTRACT (0 + CONFIG[4 + i*(2 + 2*num_bits) + 1])
       `define PORT_SIZE_A      (0 + CONFIG[4 + i*(2 + 2*num_bits) + 2 +: num_bits])
       `define PORT_SIZE_B      (0 + CONFIG[4 + i*(2 + 2*num_bits) + 2 + num_bits +: num_bits])
       `define PORT_OFFSET_A    (0 + port_offsets[2*i*num_abits +: num_abits])
       `define PORT_OFFSET_B    (0 + port_offsets[2*i*num_abits + num_abits +: num_abits])
       
       integer i, j;
       reg [Y_WIDTH-1:0] tmp_a, tmp_b;
       
       always @* begin
           Y = 0;
           for (i = 0; i < num_ports; i = i+1)
           begin
               tmp_a = 0;
               tmp_b = 0;
       
               for (j = 0; j < `PORT_SIZE_A; j = j+1)
                   tmp_a[j] = A[`PORT_OFFSET_A + j];
       
               if (`PORT_IS_SIGNED && `PORT_SIZE_A > 0)
                   for (j = `PORT_SIZE_A; j < Y_WIDTH; j = j+1)
                       tmp_a[j] = tmp_a[`PORT_SIZE_A-1];
       
               for (j = 0; j < `PORT_SIZE_B; j = j+1)
                   tmp_b[j] = A[`PORT_OFFSET_B + j];
       
               if (`PORT_IS_SIGNED && `PORT_SIZE_B > 0)
                   for (j = `PORT_SIZE_B; j < Y_WIDTH; j = j+1)
                       tmp_b[j] = tmp_b[`PORT_SIZE_B-1];
       
               if (`PORT_SIZE_B > 0)
                   tmp_a = tmp_a * tmp_b;
       
               if (`PORT_DO_SUBTRACT)
                   Y = Y - tmp_a;
               else
                   Y = Y + tmp_a;
           end
           for (i = 0; i < B_WIDTH; i = i+1) begin
               Y = Y + B[i];
           end
       end
       
       `undef PORT_IS_SIGNED
       `undef PORT_DO_SUBTRACT
       `undef PORT_SIZE_A
       `undef PORT_SIZE_B
       `undef PORT_OFFSET_A
       `undef PORT_OFFSET_B
       
   endmodule

.. note::

   This page was auto-generated from the output of
   ``help $macc``.
