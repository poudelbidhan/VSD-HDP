## Day 6: RISC_V Design Synthesis and Gate Level Simulation 

Here, we will do the synthesis and gate-level simulation of our RISC-V RV32I design file. 

First, we copy our design verilog and testbench file to our working directory. I have placed bidhan_rv32i.v and bidhan_rv32i_tb.v files inside the synthesis folder.

 ![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/43df5a93-e3da-42da-9750-0678c02e5d8d)


 ### Functional Simulation 

 Functional Simulation: 
file:///home/bidhan/Pictures/Screenshots/Screenshot%20from%202024-07-18%2011-00-16.png
![image](https://github.com/user-attachments/assets/ef33d361-c5a1-43cf-9cfb-9bd553fe67c9)


 
 1. file:///home/bidhan/Pictures/Screenshots/Screenshot%20from%202024-07-18%2010-37-41.png![image](https://github.com/user-attachments/assets/1f7253fb-52a6-48fe-b864-d9686d6cc3d5)





 2. 

 
     iverilog -o bidhan_rv32i bidhan_rv32i.v bidhan_rv32i_tb.v
     ./bidhan_rv32i 
     gtkwave rv32_i.vcd 

Simulation Output: 






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

 We do the gate-level simulation to verify the logical correctness of the design after synthesizing the design. 

file:///home/bidhan/Pictures/Screenshots/Screenshot%20from%202024-07-18%2010-39-06.png![image](https://github.com/user-attachments/assets/f06c6c0b-a791-4345-95c2-5fa74ec42cc1)


file:///home/bidhan/Pictures/Screenshots/Screenshot%20from%202024-07-18%2011-00-16.png![image](https://github.com/user-attachments/assets/2e4f130e-2a5f-4b43-9def-eea35d3d7d26)


Here we can see pre-synthesis and post-synthesis simulation result match and we are good to move forward.

 

  
