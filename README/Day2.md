## Day 2: Timing libs, Hierarchical vs. Flat Synthesis, Flip-Flop coding styles

### Hierarchical vs. Flat Synthesis
Here we observe how Yosys tool performs synthesis and generates the netlist for multi-modules with and without preserving the design hierarchy. 

1. Hierarchical Synthesis

        read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        read_verilog multiple_modules.v
        synth -top multiple_modules
        abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        write_verilog -noattr multiple_modules_hier.v
        show -stretch multiple_modules
        show sub_module1
        show sub_module2

Synthesis preserving Hierarchy 

![Screenshot from 2024-06-15 07-12-20](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/63355063-ed76-40ce-8a7a-4dffa290ffff)

![Screenshot from 2024-06-15 07-12-45](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/dc626e92-a84c-467a-a465-4066a89e88b1)

![Screenshot from 2024-06-15 07-13-11](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/935cac03-6372-48cf-b153-2ea66d7bc814)

2. Flattened

       flatten
        write_verilog -noattr multiple_modules_flat.v
        show -stretch multiple_modules

![Screenshot from 2024-06-15 07-19-51](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/e5fc1996-d072-4974-b8f3-aed6b54319e0)

