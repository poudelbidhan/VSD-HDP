# Day 1

## Introduction to Verilog RTL Design and Synthesis


Verilog RTL (Register Transfer Level) design involves describing the digital logic of a circuit at a high level of abstraction using Verilog, a hardware description language (HDL).

### 1. Writing Verilog RTL Code
Tool: Text Editor or IDE (e.g., Visual Studio Code with Verilog extensions)

Description: Write the Verilog code to describe the digital logic of the design. This code includes module definitions, wire/reg declarations, and procedural blocks (e.g., always, initial).
   
### 2. Simulation and Verification
Tool: Icarus Verilog, GTKWave

Description: Simulation: Use tools like Icarus Verilog to compile and simulate the Verilog code. This step involves creating testbenches that apply stimuli to the design and observe its behavior.

Waveform Viewing: Use GTKWave to visualize the simulation results and verify the functionality of the design.


![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/8c5bc414-7f6e-49f5-b6a7-90fbe11e5633)


### Functional Simulation of RTL Design Using iVerilog & gtkWave

1. Clone the GitHub repo with skywater130-based library files and example designs with corresponding test benches.
    ```
    git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
    ```
2. Use iverilog to read and interpret source and testbench file and generate a compiled output. 
    Here we are using good_mux.v as an example design file.
  
           iverilog good_mux.v tb_good_mux.v
   
4. The compiled output file is then executed to perform verilog simulation which generates .vcd file.

        ./a.out

5. Generated vcd files can be viewed using gtkwave
   
       gtkwave tb_good_mux.vcd

    
![Screenshot from 2024-06-14 06-41-57](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/bdfe72fa-81f3-40c0-a6e4-807e9dcbb577)





## Logic Synthesis using Yosys

Logic synthesis is a process in digital design where high-level descriptions of a circuit (usually written in Hardware Description Languages like Verilog or VHDL) are transformed into a gate-level representation. This gate-level netlist is composed of logic gates like AND, OR, NOT, flip-flops, etc., which can be directly implemented in physical hardware.

Key Steps in Logic Synthesis
### 1. Parsing and Elaboration:

The HDL code is parsed to understand the design structure, hierarchy, and logic.
Elaboration resolves all HDL constructs, instantiates modules, and creates a complete design hierarchy.

### 2. Technology Mapping:

The design is mapped to a specific technology library that defines the available logic gates and their characteristics (e.g., timing, power, area).

### 3. Optimization:

The synthesized design is optimized for various parameters like area, speed, and power. This includes logic minimization, retiming, and other transformations to improve performance and efficiency.

### 4. Netlist Generation:

The final output is a gate-level netlist, which is a textual description of the circuit in terms of logic gates and their interconnections.

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/0573991d-bee8-41fe-8288-8f207b5714d7)

Here we will perform gate-level synthesis of our simulated example design using Yosys and Sky130 library file
1. Invoke Yosys shell
   
       yosys

2. Read the libraray file

        read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib

3. Read Design File

       read_verilog good_mux.v

4. Perform the Synthesis

       synth -top good_mux

5. Generate the gate-level Netlist

       abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
![Screenshot from 2024-06-14 12-49-53](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/ffa42d42-8dfd-408c-a662-27f189aefb5c)


6. Graphical Diagram realized by the tool

       yosys> show

![Screenshot from 2024-06-14 07-47-13](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/1cf08dab-fdc2-4e32-bf09-5d4369bb6c04)

7. Generate output Netlist

       write_verilog -noattr good_mux_netlist.v

    Generated Netlist:
   
![Screenshot from 2024-06-14 12-58-30](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/e853522d-c84e-4a23-9f9b-e52d8e32f859)


