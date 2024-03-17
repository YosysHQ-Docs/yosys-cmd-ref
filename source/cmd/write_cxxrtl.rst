===================================================
write_cxxrtl - convert design to C++ RTL simulation
===================================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: write_cxxrtl
    :title: convert design to C++ RTL simulation



    .. code:: yoscrypt

        write_cxxrtl [options] [filename]

    ::

        Write C++ code that simulates the design. The generated code requires a driver
        that instantiates the design, toggles its clock, and interacts with its ports.

        The following driver may be used as an example for a design with a single clock
        driving rising edge triggered flip-flops:

            #include "top.cc"

            int main() {
              cxxrtl_design::p_top top;
              top.step();
              while (1) {
                /* user logic */
                top.p_clk.set(false);
                top.step();
                top.p_clk.set(true);
                top.step();
              }
            }

        Note that CXXRTL simulations, just like the hardware they are simulating, are
        subject to race conditions. If, in the example above, the user logic would run
        simultaneously with the rising edge of the clock, the design would malfunction.

        This backend supports replacing parts of the design with black boxes implemented
        in C++. If a module marked as a CXXRTL black box, its implementation is ignored,
        and the generated code consists only of an interface and a factory function.
        The driver must implement the factory function that creates an implementation of
        the black box, taking into account the parameters it is instantiated with.

        For example, the following Verilog code defines a CXXRTL black box interface for
        a synchronous debug sink:

            (* cxxrtl_blackbox *)
            module debug(...);
              (* cxxrtl_edge = "p" *) input clk;
              input en;
              input [7:0] i_data;
              (* cxxrtl_sync *) output [7:0] o_data;
            endmodule

        For this HDL interface, this backend will generate the following C++ interface:

            struct bb_p_debug : public module {
              value<1> p_clk;
              bool posedge_p_clk() const { /* ... */ }
              value<1> p_en;
              value<8> p_i_data;
              wire<8> p_o_data;

              bool eval(performer *performer) override;
              virtual bool commit(observer &observer);
              bool commit() override;

              static std::unique_ptr<bb_p_debug>
              create(std::string name, metadata_map parameters, metadata_map attributes);
            };

        The `create' function must be implemented by the driver. For example, it could
        always provide an implementation logging the values to standard error stream:

            namespace cxxrtl_design {

            struct stderr_debug : public bb_p_debug {
              bool eval(performer *performer) override {
                if (posedge_p_clk() && p_en)
                  fprintf(stderr, "debug: %02x\n", p_i_data.data[0]);
                p_o_data.next = p_i_data;
                return bb_p_debug::eval(performer);
              }
            };

            std::unique_ptr<bb_p_debug>
            bb_p_debug::create(std::string name, cxxrtl::metadata_map parameters,
                               cxxrtl::metadata_map attributes) {
              return std::make_unique<stderr_debug>();
            }

            }

        For complex applications of black boxes, it is possible to parameterize their
        port widths. For example, the following Verilog code defines a CXXRTL black box
        interface for a configurable width debug sink:

            (* cxxrtl_blackbox, cxxrtl_template = "WIDTH" *)
            module debug(...);
              parameter WIDTH = 8;
              (* cxxrtl_edge = "p" *) input clk;
              input en;
              (* cxxrtl_width = "WIDTH" *) input [WIDTH - 1:0] i_data;
              (* cxxrtl_width = "WIDTH" *) output [WIDTH - 1:0] o_data;
            endmodule

        For this parametric HDL interface, this backend will generate the following C++
        interface (only the differences are shown):

            template<size_t WIDTH>
            struct bb_p_debug : public module {
              // ...
              value<WIDTH> p_i_data;
              wire<WIDTH> p_o_data;
              // ...
              static std::unique_ptr<bb_p_debug<WIDTH>>
              create(std::string name, metadata_map parameters, metadata_map attributes);
            };

        The `create' function must be implemented by the driver, specialized for every
        possible combination of template parameters. (Specialization is necessary to
        enable separate compilation of generated code and black box implementations.)

            template<size_t SIZE>
            struct stderr_debug : public bb_p_debug<SIZE> {
              // ...
            };

            template<>
            std::unique_ptr<bb_p_debug<8>>
            bb_p_debug<8>::create(std::string name, cxxrtl::metadata_map parameters,
                                  cxxrtl::metadata_map attributes) {
              return std::make_unique<stderr_debug<8>>();
            }

        The following attributes are recognized by this backend:

            cxxrtl_blackbox
                only valid on modules. if specified, the module contents are ignored,
                and the generated code includes only the module interface and a factory
                function, which will be called to instantiate the module.

            cxxrtl_edge
                only valid on inputs of black boxes. must be one of "p", "n", "a".
                if specified on signal `clk`, the generated code includes edge detectors
                `posedge_p_clk()` (if "p"), `negedge_p_clk()` (if "n"), or both (if
                "a"), simplifying implementation of clocked black boxes.

            cxxrtl_template
                only valid on black boxes. must contain a space separated sequence of
                identifiers that have a corresponding black box parameters. for each
                of them, the generated code includes a `size_t` template parameter.

            cxxrtl_width
                only valid on ports of black boxes. must be a constant expression, which
                is directly inserted into generated code.

            cxxrtl_comb, cxxrtl_sync
                only valid on outputs of black boxes. if specified, indicates that every
                bit of the output port is driven, correspondingly, by combinatorial or
                synchronous logic. this knowledge is used for scheduling optimizations.
                if neither is specified, the output will be pessimistically treated as
                driven by both combinatorial and synchronous logic.

        The following options are supported by this backend:


    .. code:: yoscrypt

        -print-wire-types, -print-debug-wire-types

    ::

            enable additional debug logging, for pass developers.


    .. code:: yoscrypt

        -header

    ::

            generate separate interface (.h) and implementation (.cc) files.
            if specified, the backend must be called with a filename, and filename
            of the interface is derived from filename of the implementation.
            otherwise, interface and implementation are generated together.


    .. code:: yoscrypt

        -namespace <ns-name>

    ::

            place the generated code into namespace <ns-name>. if not specified,
            "cxxrtl_design" is used.


    .. code:: yoscrypt

        -print-output <stream>

    ::

            $print cells in the generated code direct their output to <stream>.
            must be one of "std::cout", "std::cerr". if not specified,
            "std::cout" is used. explicitly provided performer overrides this.


    .. code:: yoscrypt

        -nohierarchy

    ::

            use design hierarchy as-is. in most designs, a top module should be
            present as it is exposed through the C API and has unbuffered outputs
            for improved performance; it will be determined automatically if absent.


    .. code:: yoscrypt

        -noflatten

    ::

            don't flatten the design. fully flattened designs can evaluate within
            one delta cycle if they have no combinatorial feedback.
            note that the debug interface and waveform dumps use full hierarchical
            names for all wires even in flattened designs.


    .. code:: yoscrypt

        -noproc

    ::

            don't convert processes to netlists. in most designs, converting
            processes significantly improves evaluation performance at the cost of
            slight increase in compilation time.


    .. code:: yoscrypt

        -O <level>

    ::

            set the optimization level. the default is -O6. higher optimization
            levels dramatically decrease compile and run time, and highest level
            possible for a design should be used.


    .. code:: yoscrypt

        -O0

    ::

            no optimization.


    .. code:: yoscrypt

        -O1

    ::

            unbuffer internal wires if possible.


    .. code:: yoscrypt

        -O2

    ::

            like -O1, and localize internal wires if possible.


    .. code:: yoscrypt

        -O3

    ::

            like -O2, and inline internal wires if possible.


    .. code:: yoscrypt

        -O4

    ::

            like -O3, and unbuffer public wires not marked (*keep*) if possible.


    .. code:: yoscrypt

        -O5

    ::

            like -O4, and localize public wires not marked (*keep*) if possible.


    .. code:: yoscrypt

        -O6

    ::

            like -O5, and inline public wires not marked (*keep*) if possible.


    .. code:: yoscrypt

        -g <level>

    ::

            set the debug level. the default is -g4. higher debug levels provide
            more visibility and generate more code, but do not pessimize evaluation.


    .. code:: yoscrypt

        -g0

    ::

            no debug information. the C API is disabled.


    .. code:: yoscrypt

        -g1

    ::

            include bare minimum of debug information necessary to access all design
            state. the C API is enabled.


    .. code:: yoscrypt

        -g2

    ::

            like -g1, but include debug information for all public wires that are
            directly accessible through the C++ interface.


    .. code:: yoscrypt

        -g3

    ::

            like -g2, and include debug information for public wires that are tied
            to a constant or another public wire.


    .. code:: yoscrypt

        -g4

    ::

            like -g3, and compute debug information on demand for all public wires
            that were optimized out.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_cxxrtl [options] [filename]
        
        Write C++ code that simulates the design. The generated code requires a driver
        that instantiates the design, toggles its clock, and interacts with its ports.
        
        The following driver may be used as an example for a design with a single clock
        driving rising edge triggered flip-flops:
        
            #include "top.cc"
        
            int main() {
              cxxrtl_design::p_top top;
              top.step();
              while (1) {
                /* user logic */
                top.p_clk.set(false);
                top.step();
                top.p_clk.set(true);
                top.step();
              }
            }
        
        Note that CXXRTL simulations, just like the hardware they are simulating, are
        subject to race conditions. If, in the example above, the user logic would run
        simultaneously with the rising edge of the clock, the design would malfunction.
        
        This backend supports replacing parts of the design with black boxes implemented
        in C++. If a module marked as a CXXRTL black box, its implementation is ignored,
        and the generated code consists only of an interface and a factory function.
        The driver must implement the factory function that creates an implementation of
        the black box, taking into account the parameters it is instantiated with.
        
        For example, the following Verilog code defines a CXXRTL black box interface for
        a synchronous debug sink:
        
            (* cxxrtl_blackbox *)
            module debug(...);
              (* cxxrtl_edge = "p" *) input clk;
              input en;
              input [7:0] i_data;
              (* cxxrtl_sync *) output [7:0] o_data;
            endmodule
        
        For this HDL interface, this backend will generate the following C++ interface:
        
            struct bb_p_debug : public module {
              value<1> p_clk;
              bool posedge_p_clk() const { /* ... */ }
              value<1> p_en;
              value<8> p_i_data;
              wire<8> p_o_data;
        
              bool eval(performer *performer) override;
              virtual bool commit(observer &observer);
              bool commit() override;
        
              static std::unique_ptr<bb_p_debug>
              create(std::string name, metadata_map parameters, metadata_map attributes);
            };
        
        The `create' function must be implemented by the driver. For example, it could
        always provide an implementation logging the values to standard error stream:
        
            namespace cxxrtl_design {
        
            struct stderr_debug : public bb_p_debug {
              bool eval(performer *performer) override {
                if (posedge_p_clk() && p_en)
                  fprintf(stderr, "debug: %02x\n", p_i_data.data[0]);
                p_o_data.next = p_i_data;
                return bb_p_debug::eval(performer);
              }
            };
        
            std::unique_ptr<bb_p_debug>
            bb_p_debug::create(std::string name, cxxrtl::metadata_map parameters,
                               cxxrtl::metadata_map attributes) {
              return std::make_unique<stderr_debug>();
            }
        
            }
        
        For complex applications of black boxes, it is possible to parameterize their
        port widths. For example, the following Verilog code defines a CXXRTL black box
        interface for a configurable width debug sink:
        
            (* cxxrtl_blackbox, cxxrtl_template = "WIDTH" *)
            module debug(...);
              parameter WIDTH = 8;
              (* cxxrtl_edge = "p" *) input clk;
              input en;
              (* cxxrtl_width = "WIDTH" *) input [WIDTH - 1:0] i_data;
              (* cxxrtl_width = "WIDTH" *) output [WIDTH - 1:0] o_data;
            endmodule
        
        For this parametric HDL interface, this backend will generate the following C++
        interface (only the differences are shown):
        
            template<size_t WIDTH>
            struct bb_p_debug : public module {
              // ...
              value<WIDTH> p_i_data;
              wire<WIDTH> p_o_data;
              // ...
              static std::unique_ptr<bb_p_debug<WIDTH>>
              create(std::string name, metadata_map parameters, metadata_map attributes);
            };
        
        The `create' function must be implemented by the driver, specialized for every
        possible combination of template parameters. (Specialization is necessary to
        enable separate compilation of generated code and black box implementations.)
        
            template<size_t SIZE>
            struct stderr_debug : public bb_p_debug<SIZE> {
              // ...
            };
        
            template<>
            std::unique_ptr<bb_p_debug<8>>
            bb_p_debug<8>::create(std::string name, cxxrtl::metadata_map parameters,
                                  cxxrtl::metadata_map attributes) {
              return std::make_unique<stderr_debug<8>>();
            }
        
        The following attributes are recognized by this backend:
        
            cxxrtl_blackbox
                only valid on modules. if specified, the module contents are ignored,
                and the generated code includes only the module interface and a factory
                function, which will be called to instantiate the module.
        
            cxxrtl_edge
                only valid on inputs of black boxes. must be one of "p", "n", "a".
                if specified on signal `clk`, the generated code includes edge detectors
                `posedge_p_clk()` (if "p"), `negedge_p_clk()` (if "n"), or both (if
                "a"), simplifying implementation of clocked black boxes.
        
            cxxrtl_template
                only valid on black boxes. must contain a space separated sequence of
                identifiers that have a corresponding black box parameters. for each
                of them, the generated code includes a `size_t` template parameter.
        
            cxxrtl_width
                only valid on ports of black boxes. must be a constant expression, which
                is directly inserted into generated code.
        
            cxxrtl_comb, cxxrtl_sync
                only valid on outputs of black boxes. if specified, indicates that every
                bit of the output port is driven, correspondingly, by combinatorial or
                synchronous logic. this knowledge is used for scheduling optimizations.
                if neither is specified, the output will be pessimistically treated as
                driven by both combinatorial and synchronous logic.
        
        The following options are supported by this backend:
        
            -print-wire-types, -print-debug-wire-types
                enable additional debug logging, for pass developers.
        
            -header
                generate separate interface (.h) and implementation (.cc) files.
                if specified, the backend must be called with a filename, and filename
                of the interface is derived from filename of the implementation.
                otherwise, interface and implementation are generated together.
        
            -namespace <ns-name>
                place the generated code into namespace <ns-name>. if not specified,
                "cxxrtl_design" is used.
        
            -print-output <stream>
                $print cells in the generated code direct their output to <stream>.
                must be one of "std::cout", "std::cerr". if not specified,
                "std::cout" is used. explicitly provided performer overrides this.
        
            -nohierarchy
                use design hierarchy as-is. in most designs, a top module should be
                present as it is exposed through the C API and has unbuffered outputs
                for improved performance; it will be determined automatically if absent.
        
            -noflatten
                don't flatten the design. fully flattened designs can evaluate within
                one delta cycle if they have no combinatorial feedback.
                note that the debug interface and waveform dumps use full hierarchical
                names for all wires even in flattened designs.
        
            -noproc
                don't convert processes to netlists. in most designs, converting
                processes significantly improves evaluation performance at the cost of
                slight increase in compilation time.
        
            -O <level>
                set the optimization level. the default is -O6. higher optimization
                levels dramatically decrease compile and run time, and highest level
                possible for a design should be used.
        
            -O0
                no optimization.
        
            -O1
                unbuffer internal wires if possible.
        
            -O2
                like -O1, and localize internal wires if possible.
        
            -O3
                like -O2, and inline internal wires if possible.
        
            -O4
                like -O3, and unbuffer public wires not marked (*keep*) if possible.
        
            -O5
                like -O4, and localize public wires not marked (*keep*) if possible.
        
            -O6
                like -O5, and inline public wires not marked (*keep*) if possible.
        
            -g <level>
                set the debug level. the default is -g4. higher debug levels provide
                more visibility and generate more code, but do not pessimize evaluation.
        
            -g0
                no debug information. the C API is disabled.
        
            -g1
                include bare minimum of debug information necessary to access all design
                state. the C API is enabled.
        
            -g2
                like -g1, but include debug information for all public wires that are
                directly accessible through the C++ interface.
        
            -g3
                like -g2, and include debug information for public wires that are tied
                to a constant or another public wire.
        
            -g4
                like -g3, and compute debug information on demand for all public wires
                that were optimized out.
        
