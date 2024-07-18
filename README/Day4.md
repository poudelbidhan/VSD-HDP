


## Day 4: Gate Level Simulation (GLS) and Synthesis-Simulation mismatch

### Gate Level Simulation 
Gate-level simulation is a process of simulating a digital circuit at the level of individual logic gates and their interconnections. It provides a detailed and accurate representation of the circuit's behavior, considering the actual gate delays and the interconnection delays. This type of simulation is performed after the synthesis process and is crucial for verifying the timing and functionality of the design before moving on to physical implementation

![image](https://github.com/user-attachments/assets/c5b6b576-f547-4020-b6e0-84b0ff2ecd7b)


### Synthesis - Simulation Mismatch 

Synthesis-simulation mismatch refers to discrepancies between the behavior of a digital design during RTL simulation and its behavior after synthesis. This mismatch can cause functional errors that may not be caught until later stages of the design flow, leading to costly debugging and potential redesigns. Understanding the common causes and strategies to avoid synthesis-simulation mismatches is critical for reliable digital design.

Common Causes of Synthesis-Simulation Mismatch

1. Uninitialized Variables:

In simulation, uninitialized variables typically take on an unknown value (X). During synthesis, these variables may be optimized away or set to a default value, leading to different behaviors.

2. Timing and Delays:

RTL simulation may use zero-delay or small delays for certain operations, while the synthesized netlist reflects actual gate delays. This discrepancy can cause timing-related mismatches.

3. Blocking vs. Non-blocking Assignments:

Improper use of blocking (=) and non-blocking (<=) assignments in sequential logic can lead to differences in behavior. Non-blocking assignments should be used for sequential logic to avoid race conditions.

4. Asynchronous vs. Synchronous Resets:

Differences in handling asynchronous and synchronous resets can cause mismatches. Simulation might handle reset conditions differently compared to the synthesized hardware.

5. Latch Inference:

Unintentionally inferring latches in the RTL code can lead to mismatches. Synthesis tools might optimize or interpret these latches differently than how they behave in simulation.

6. Sensitivity List Issues:

Incorrect or incomplete sensitivity lists in always blocks can cause differences in behavior between simulation and synthesis.

7. Vendor-specific Primitives and Constructs:

Using vendor-specific primitives or constructs that are not supported or behave differently in the synthesis tool compared to the simulator.

8. Constant Propagation and Optimization:

The synthesis tool may optimize certain constants and propagate them, leading to different behavior than what was simulated.

9. Tool-specific Interpretations:

Different tools (simulators and synthesizers) may interpret HDL constructs slightly differently, leading to mismatches.

### labs 

    iverilog <Path to primitives.v file > <Path to sky130_fd_sc_hd__tt_025C_1v80.lib> <Name of netlist:ternary_operator_mux_net.v> <Name of testbench: tb_ternary_operator_mux.v>
    ./a.out
    gtkwave tb_ternary_operator_mux.vdc

lab1: ternary_operator_mux.v 

Simulation Result
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/c7a54d5c-aa9f-4dd2-8c80-409a605d6f8e)


Synthesis Result: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/1e82486a-d557-423a-970b-b982b899bca9)

GLS Simulation Result : 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/09045fac-d818-4747-9c8b-3e98c62da959)





lab2 : bad_mux.v 
RTL Simulation : 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/5bb03538-1f00-4788-ab00-91204bc6d619)


Synthesis Result: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/9012430f-3970-4bc6-a3fb-113c7a478b46)


GLS Result: 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/8e2412a1-c03c-420e-ba27-d108daceca47)



lab: blocking_caveat.v 

RTL Simulation: 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/4df0c4df-233c-450d-9a27-1c13a9138b84)


Synthesis Result: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/941144b9-ab81-438a-8377-b77dcdb9c9b8)


GLS Result: 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/64972f06-694a-4305-8a2f-88168870325e)

