
## Day 3: Combinational and Sequential Optimization 

Optimization in digital design is crucial for improving performance, reducing the area, and minimizing the power consumption of a circuit. Combinational and sequential optimizations are two primary categories of optimizations applied to different parts of the design.

### Combinational Optimization

Combinational optimization focuses on combinational logic, which consists of logic gates and circuits that do not have memory elements or feedback loops. These circuits compute their outputs solely based on the current inputs.

Techniques for Combinational Optimization

1. Logic Minimization:

Reducing the number of logic gates and simplifying boolean expressions using techniques like Karnaugh maps, Quine-McCluskey algorithm, and Espresso heuristic logic minimizer.

2. Constant Propagation:

Simplifying the logic by propagating constant values through the circuit. If a logic gate has constant inputs, its output can be computed and replaced by a constant.

3. Common Subexpression Elimination:

Identifying and eliminating redundant logic that computes the same expression multiple times. This reduces the overall gate count.

4. Algebraic Simplification:

Applying Boolean algebra rules to simplify expressions and reduce the number of gates. For example, using the distributive, associative, and De Morgan's laws.

5. Technology Mapping:

Mapping the logic to specific gates available in the target technology library, selecting gates that provide the best trade-off between speed, area, and power.

6. Redundancy Removal:

Identifying and eliminating redundant logic that does not contribute to the primary outputs, reducing the circuit complexity.

7. Retiming:

Repositioning the registers in the circuit to improve performance without changing the functionality. This can help in balancing the delay across the circuit.

### Sequential Optimization
Sequential optimization focuses on circuits with memory elements (e.g., flip-flops, latches) and involves improving the design's timing and area while maintaining its sequential behavior.

Techniques for Sequential Optimization
1. State Minimization:

Reducing the number of states in a finite state machine (FSM) while preserving its behavior. Fewer states result in simpler logic and fewer flip-flops.

2. Clock Gating:

Reducing power consumption by disabling the clock signal to portions of the circuit that are not active, thereby reducing switching activity.

3. Retiming:

Moving registers across combinational logic to balance the delays and improve the overall timing of the circuit. Retiming can help meet timing constraints and reduce the critical path length.

4. Register Sharing:

Sharing registers among different parts of the circuit to reduce the total number of registers needed. This can be done by merging registers that hold the same or similar data.

5. Pipelining:

Splitting the combinational logic into multiple stages separated by registers, allowing higher clock frequencies and improved throughput.

6. Resource Sharing:

Using the same hardware resources (e.g., arithmetic units) for different operations at different times, reducing the overall area.

7. Sequential Logic Optimization:

Simplifying the sequential logic by merging equivalent states, removing unreachable states, and optimizing state transitions.


### labs: 

1. lab1 : opt_check.v
    
                             
        module opt_check (input a , input b , output y);
                assign y = a?b:0;
        endmodule

Synthesis Result
![Screenshot from 2024-06-20 19-40-58](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/e30e827c-81c0-4e72-bd98-5703037fe754)


2. lab2 : opt_check2.v


synthesis Result: 
![Screenshot from 2024-06-20 19-44-50](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/795d00b8-5256-49b8-97d5-d25bd8f3323f)


3. lab3: opt_check3.v

Synthesis Result: 
![Screenshot from 2024-06-20 19-47-15](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/94e1719f-23d6-474a-99df-91ff6398bb3d)


4. lab 4:

Synthesis Result: 
![Screenshot from 2024-06-20 19-59-33](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/9a8eb8bf-a55b-4e34-a80b-521cd224358d)


5. lab 5:

Synthesis Result: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/f8d8143d-4929-4fa9-b428-837a90b9aed7)



6. lab 6;
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/e9e2cf19-4dbc-4590-8c7c-eba2ddf0b837)




### Sequential Logic Optimization 

lab1. dff_const1.v

Simulation Result 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/dfe2a5aa-9832-478c-bb4b-a0d58bdf77c0)


Synthesis Result: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/49765ce4-6aeb-428e-9065-fb6affe935da)

        
lab2 : dff_const2.v

Simulation Result 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/2444420d-c5c8-44c0-8298-1be7bf6e3369)



Synthesis Result: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/99396dbb-6fa0-4124-827a-2426285f8345)


lab3: dff_const3.v

simulation Result
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/2c9aebb0-28ae-47a3-9dcb-a7b09e5c3456)


Synthesis Result
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/ed67ec45-c022-46be-b641-edb8fa208915)


lab4 : dff_const4.v

Simulation Result 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/77e3b51b-766f-4978-a914-29388356c900)


Synthesis Result
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/15562af8-5d83-467a-a7dc-abbeb5227577)


lab 5: dff_const5.v
Simulation Result: 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/b064f121-f2bd-4966-8f08-46c85baeda81)


Synthesis Result: 
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/1f427922-13c4-45ab-928a-6615e97478a6)



lab 6: Counter_opt.v

Simulation Result
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/24b89303-711d-44d9-bd61-2ab61c176c1b)


Synthesis Result
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/28f0fbf4-d28a-4e1d-81fb-ad27733c20b2)
