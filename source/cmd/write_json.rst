========================================
write_json - write design to a JSON file
========================================

.. raw:: latex

    \begin{comment}

.. cmd:def:: write_json
    :title: write design to a JSON file



    .. code:: yoscrypt

        write_json [options] [filename]

    ::

        Write a JSON netlist of the current design.


    .. code:: yoscrypt

        -aig

    ::

            include AIG models for the different gate types


    .. code:: yoscrypt

        -compat-int

    ::

            emit 32-bit or smaller fully-defined parameter values directly
            as JSON numbers (for compatibility with old parsers)



    ::

        The general syntax of the JSON output created by this command is as follows:

            {
              "creator": "Yosys <version info>",
              "modules": {
                <module_name>: {
                  "attributes": {
                    <attribute_name>: <attribute_value>,
                    ...
                  },
                  "parameter_default_values": {
                    <parameter_name>: <parameter_value>,
                    ...
                  },
                  "ports": {
                    <port_name>: <port_details>,
                    ...
                  },
                  "cells": {
                    <cell_name>: <cell_details>,
                    ...
                  },
                  "memories": {
                    <memory_name>: <memory_details>,
                    ...
                  },
                  "netnames": {
                    <net_name>: <net_details>,
                    ...
                  }
                }
              },
              "models": {
                ...
              },
            }

        Where <port_details> is:

            {
              "direction": <"input" | "output" | "inout">,
              "bits": <bit_vector>
              "offset": <the lowest bit index in use, if non-0>
              "upto": <1 if the port bit indexing is MSB-first>
              "signed": <1 if the port is signed>
            }

        The "offset" and "upto" fields are skipped if their value would be 0.
        They don't affect connection semantics, and are only used to preserve original
        HDL bit indexing.And <cell_details> is:

            {
              "hide_name": <1 | 0>,
              "type": <cell_type>,
              "model": <AIG model name, if -aig option used>,
              "parameters": {
                <parameter_name>: <parameter_value>,
                ...
              },
              "attributes": {
                <attribute_name>: <attribute_value>,
                ...
              },
              "port_directions": {
                <port_name>: <"input" | "output" | "inout">,
                ...
              },
              "connections": {
                <port_name>: <bit_vector>,
                ...
              },
            }

        And <memory_details> is:

            {
              "hide_name": <1 | 0>,
              "attributes": {
                <attribute_name>: <attribute_value>,
                ...
              },
              "width": <memory width>
              "start_offset": <the lowest valid memory address>
              "size": <memory size>
            }

        And <net_details> is:

            {
              "hide_name": <1 | 0>,
              "bits": <bit_vector>
              "offset": <the lowest bit index in use, if non-0>
              "upto": <1 if the port bit indexing is MSB-first>
              "signed": <1 if the port is signed>
            }

        The "hide_name" fields are set to 1 when the name of this cell or net is
        automatically created and is likely not of interest for a regular user.

        The "port_directions" section is only included for cells for which the
        interface is known.

        Module and cell ports and nets can be single bit wide or vectors of multiple
        bits. Each individual signal bit is assigned a unique integer. The <bit_vector>
        values referenced above are vectors of this integers. Signal bits that are
        connected to a constant driver are denoted as string "0", "1", "x", or
        "z" instead of a number.

        Bit vectors (including integers) are written as string holding the binary
        representation of the value. Strings are written as strings, with an appended
        blank in cases of strings of the form /[01xz]* */.

        For example the following Verilog code:

            module test(input x, y);
              (* keep *) foo #(.P(42), .Q(1337))
                  foo_inst (.A({x, y}), .B({y, x}), .C({4'd10, {4{x}}}));
            endmodule

        Translates to the following JSON output:

            {
              "creator": "Yosys 0.9+2406 (git sha1 fb1168d8, clang 9.0.1 -fPIC -Os)",
              "modules": {
                "test": {
                  "attributes": {
                    "cells_not_processed": "00000000000000000000000000000001",
                    "src": "test.v:1.1-4.10"
                  },
                  "ports": {
                    "x": {
                      "direction": "input",
                      "bits": [ 2 ]
                    },
                    "y": {
                      "direction": "input",
                      "bits": [ 3 ]
                    }
                  },
                  "cells": {
                    "foo_inst": {
                      "hide_name": 0,
                      "type": "foo",
                      "parameters": {
                        "P": "00000000000000000000000000101010",
                        "Q": "00000000000000000000010100111001"
                      },
                      "attributes": {
                        "keep": "00000000000000000000000000000001",
                        "module_not_derived": "00000000000000000000000000000001",
                        "src": "test.v:3.1-3.55"
                      },
                      "connections": {
                        "A": [ 3, 2 ],
                        "B": [ 2, 3 ],
                        "C": [ 2, 2, 2, 2, "0", "1", "0", "1" ]
                      }
                    }
                  },
                  "netnames": {
                    "x": {
                      "hide_name": 0,
                      "bits": [ 2 ],
                      "attributes": {
                        "src": "test.v:1.19-1.20"
                      }
                    },
                    "y": {
                      "hide_name": 0,
                      "bits": [ 3 ],
                      "attributes": {
                        "src": "test.v:1.22-1.23"
                      }
                    }
                  }
                }
              }
            }

        The models are given as And-Inverter-Graphs (AIGs) in the following form:

            "models": {
              <model_name>: [
                /*   0 */ [ <node-spec> ],
                /*   1 */ [ <node-spec> ],
                /*   2 */ [ <node-spec> ],
                ...
              ],
              ...
            },

        The following node-types may be used:

            [ "port", <portname>, <bitindex>, <out-list> ]
              - the value of the specified input port bit

            [ "nport", <portname>, <bitindex>, <out-list> ]
              - the inverted value of the specified input port bit

            [ "and", <node-index>, <node-index>, <out-list> ]
              - the ANDed value of the specified nodes

            [ "nand", <node-index>, <node-index>, <out-list> ]
              - the inverted ANDed value of the specified nodes

            [ "true", <out-list> ]
              - the constant value 1

            [ "false", <out-list> ]
              - the constant value 0

        All nodes appear in topological order. I.e. only nodes with smaller indices
        are referenced by "and" and "nand" nodes.

        The optional <out-list> at the end of a node specification is a list of
        output portname and bitindex pairs, specifying the outputs driven by this node.

        For example, the following is the model for a 3-input 3-output $reduce_and cell
        inferred by the following code:

            module test(input [2:0] in, output [2:0] out);
              assign in = &out;
            endmodule

            "$reduce_and:3U:3": [
              /*   0 */ [ "port", "A", 0 ],
              /*   1 */ [ "port", "A", 1 ],
              /*   2 */ [ "and", 0, 1 ],
              /*   3 */ [ "port", "A", 2 ],
              /*   4 */ [ "and", 2, 3, "Y", 0 ],
              /*   5 */ [ "false", "Y", 1, "Y", 2 ]
            ]

        Future version of Yosys might add support for additional fields in the JSON
        format. A program processing this format must ignore all unknown fields.

.. raw:: latex

    \end{comment}

.. only:: latex

    ::

        
            write_json [options] [filename]
        
        Write a JSON netlist of the current design.
        
            -aig
                include AIG models for the different gate types
        
            -compat-int
                emit 32-bit or smaller fully-defined parameter values directly
                as JSON numbers (for compatibility with old parsers)
        
        
        The general syntax of the JSON output created by this command is as follows:
        
            {
              "creator": "Yosys <version info>",
              "modules": {
                <module_name>: {
                  "attributes": {
                    <attribute_name>: <attribute_value>,
                    ...
                  },
                  "parameter_default_values": {
                    <parameter_name>: <parameter_value>,
                    ...
                  },
                  "ports": {
                    <port_name>: <port_details>,
                    ...
                  },
                  "cells": {
                    <cell_name>: <cell_details>,
                    ...
                  },
                  "memories": {
                    <memory_name>: <memory_details>,
                    ...
                  },
                  "netnames": {
                    <net_name>: <net_details>,
                    ...
                  }
                }
              },
              "models": {
                ...
              },
            }
        
        Where <port_details> is:
        
            {
              "direction": <"input" | "output" | "inout">,
              "bits": <bit_vector>
              "offset": <the lowest bit index in use, if non-0>
              "upto": <1 if the port bit indexing is MSB-first>
              "signed": <1 if the port is signed>
            }
        
        The "offset" and "upto" fields are skipped if their value would be 0.
        They don't affect connection semantics, and are only used to preserve original
        HDL bit indexing.And <cell_details> is:
        
            {
              "hide_name": <1 | 0>,
              "type": <cell_type>,
              "model": <AIG model name, if -aig option used>,
              "parameters": {
                <parameter_name>: <parameter_value>,
                ...
              },
              "attributes": {
                <attribute_name>: <attribute_value>,
                ...
              },
              "port_directions": {
                <port_name>: <"input" | "output" | "inout">,
                ...
              },
              "connections": {
                <port_name>: <bit_vector>,
                ...
              },
            }
        
        And <memory_details> is:
        
            {
              "hide_name": <1 | 0>,
              "attributes": {
                <attribute_name>: <attribute_value>,
                ...
              },
              "width": <memory width>
              "start_offset": <the lowest valid memory address>
              "size": <memory size>
            }
        
        And <net_details> is:
        
            {
              "hide_name": <1 | 0>,
              "bits": <bit_vector>
              "offset": <the lowest bit index in use, if non-0>
              "upto": <1 if the port bit indexing is MSB-first>
              "signed": <1 if the port is signed>
            }
        
        The "hide_name" fields are set to 1 when the name of this cell or net is
        automatically created and is likely not of interest for a regular user.
        
        The "port_directions" section is only included for cells for which the
        interface is known.
        
        Module and cell ports and nets can be single bit wide or vectors of multiple
        bits. Each individual signal bit is assigned a unique integer. The <bit_vector>
        values referenced above are vectors of this integers. Signal bits that are
        connected to a constant driver are denoted as string "0", "1", "x", or
        "z" instead of a number.
        
        Bit vectors (including integers) are written as string holding the binary
        representation of the value. Strings are written as strings, with an appended
        blank in cases of strings of the form /[01xz]* */.
        
        For example the following Verilog code:
        
            module test(input x, y);
              (* keep *) foo #(.P(42), .Q(1337))
                  foo_inst (.A({x, y}), .B({y, x}), .C({4'd10, {4{x}}}));
            endmodule
        
        Translates to the following JSON output:
        
            {
              "creator": "Yosys 0.9+2406 (git sha1 fb1168d8, clang 9.0.1 -fPIC -Os)",
              "modules": {
                "test": {
                  "attributes": {
                    "cells_not_processed": "00000000000000000000000000000001",
                    "src": "test.v:1.1-4.10"
                  },
                  "ports": {
                    "x": {
                      "direction": "input",
                      "bits": [ 2 ]
                    },
                    "y": {
                      "direction": "input",
                      "bits": [ 3 ]
                    }
                  },
                  "cells": {
                    "foo_inst": {
                      "hide_name": 0,
                      "type": "foo",
                      "parameters": {
                        "P": "00000000000000000000000000101010",
                        "Q": "00000000000000000000010100111001"
                      },
                      "attributes": {
                        "keep": "00000000000000000000000000000001",
                        "module_not_derived": "00000000000000000000000000000001",
                        "src": "test.v:3.1-3.55"
                      },
                      "connections": {
                        "A": [ 3, 2 ],
                        "B": [ 2, 3 ],
                        "C": [ 2, 2, 2, 2, "0", "1", "0", "1" ]
                      }
                    }
                  },
                  "netnames": {
                    "x": {
                      "hide_name": 0,
                      "bits": [ 2 ],
                      "attributes": {
                        "src": "test.v:1.19-1.20"
                      }
                    },
                    "y": {
                      "hide_name": 0,
                      "bits": [ 3 ],
                      "attributes": {
                        "src": "test.v:1.22-1.23"
                      }
                    }
                  }
                }
              }
            }
        
        The models are given as And-Inverter-Graphs (AIGs) in the following form:
        
            "models": {
              <model_name>: [
                /*   0 */ [ <node-spec> ],
                /*   1 */ [ <node-spec> ],
                /*   2 */ [ <node-spec> ],
                ...
              ],
              ...
            },
        
        The following node-types may be used:
        
            [ "port", <portname>, <bitindex>, <out-list> ]
              - the value of the specified input port bit
        
            [ "nport", <portname>, <bitindex>, <out-list> ]
              - the inverted value of the specified input port bit
        
            [ "and", <node-index>, <node-index>, <out-list> ]
              - the ANDed value of the specified nodes
        
            [ "nand", <node-index>, <node-index>, <out-list> ]
              - the inverted ANDed value of the specified nodes
        
            [ "true", <out-list> ]
              - the constant value 1
        
            [ "false", <out-list> ]
              - the constant value 0
        
        All nodes appear in topological order. I.e. only nodes with smaller indices
        are referenced by "and" and "nand" nodes.
        
        The optional <out-list> at the end of a node specification is a list of
        output portname and bitindex pairs, specifying the outputs driven by this node.
        
        For example, the following is the model for a 3-input 3-output $reduce_and cell
        inferred by the following code:
        
            module test(input [2:0] in, output [2:0] out);
              assign in = &out;
            endmodule
        
            "$reduce_and:3U:3": [
              /*   0 */ [ "port", "A", 0 ],
              /*   1 */ [ "port", "A", 1 ],
              /*   2 */ [ "and", 0, 1 ],
              /*   3 */ [ "port", "A", 2 ],
              /*   4 */ [ "and", 2, 3, "Y", 0 ],
              /*   5 */ [ "false", "Y", 1, "Y", 2 ]
            ]
        
        Future version of Yosys might add support for additional fields in the JSON
        format. A program processing this format must ignore all unknown fields.
        
