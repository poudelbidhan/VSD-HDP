## Day 6: RISC_V Design Synthesis and Gate Level Simulation 

Here, we will do the synthesis and gate-level simulation of our RISC-V RV32I design file. 

First, we copy our design verilog and testbench file to our working directory. I have placed bidhan_rv32i.v and bidhan_rv32i_tb.v files inside the synthesis folder.

 ![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/43df5a93-e3da-42da-9750-0678c02e5d8d)


 ### Functional Simulation 

 Functional Simulation: 
     iverilog -o bidhan_rv32i bidhan_rv32i.v bidhan_rv32i_tb.v
     ./bidhan_rv32i 
     gtkwave rv32_i.vcd 


 ![image](https://github.com/user-attachments/assets/1f7253fb-52a6-48fe-b864-d9686d6cc3d5)







### Synthesis 

Here we do the synthesis of our design file with Yosys. 
You can do that either by running the following commands one at a time. 

    #read design
    read -sv bidhan_rv32i.v
    hierarchy -top rv32i
    #the high-level stuff
    proc; fsm; opt; memory; opt
    #mapping to internal cell library
    techmap; opt
    #mapping flip-flops to mycells.lib
    dfflibmap -liberty /home/bidhan/project/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    #mapping logic to mycells.lib
    abc -liberty /home/bidhan/project/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    #cleanup
    clean
    write_verilog -noattr bidhan_rv32i_synth.v


Or, you can create a ``` .sh ``` file with all the commands inside it and run the script once. 

    yosys
    script synthesis.sh

  In the end, we should successfully get the synthesized file named bidhan_rv32i_synth.v
  

### Gate Level Simulation 
```
iverilog <Path to primitives.v file ><Path to sky130_fd_sc_hd__tt_025C_1v80.lib><Name of netlist: bidhan_rv32i.v>
   <Name of testbench: bidhan_rv32i_tb.v>
   ./a.out
   gtkwave rv32i.vdc
```


 We do the gate-level simulation to verify the logical correctness of the design after synthesizing the design. 
![image](https://github.com/user-attachments/assets/2e4f130e-2a5f-4b43-9def-eea35d3d7d26)


Gate-level simulation output is unexpected which turned out to be an error in synthesis tool. 
The following parameters were passed to iverilog: ``` DFUNCTIONAL ``` to simulate with functional models, as behavioural tend to be buggy; and ```UNIT_DELAY```.
```
  iverilog -DFUNCTIONAL -DUNIT_DELAY=#1 <Path to primitives.v file > <Path to sky130_fd_sc_hd__tt_025C_1v80.lib> <Name of netlist: risc_v_net.v> <Name of testbench: risc_v_tb.v>
  ./a.out
  gtkwave risc_v.vdc
```
![image](https://github.com/user-attachments/assets/e6877c3a-e676-448d-abc5-5bcd88627764)


Here we can see pre-synthesis and post-synthesis simulation result match and we are good to move forward.

 

  
