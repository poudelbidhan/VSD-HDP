## Day 6: RISC_V Design Synthesis and Gate Level Simulation 

Here, we will do the synthesis and gate-level simulation of our RISC-V RV32I design file. 

First, we copy our design verilog and testbench file to our working directory. I have placed bidhan_rv32i.v and bidhan_rv32i_tb.v files inside the synthesis folder.

 ![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/43df5a93-e3da-42da-9750-0678c02e5d8d)


 ### Functional Simulation 

 | S. No. | Operation       | Hardcoded ISA  |
|--------|-----------------|----------------|
| 1      | ADD R6, R2, R1  | 32'h02208300   |
| 2      | SUB R7, R1, R2  | 32'h02209380   |
| 3      | AND R8, R1, R3  | 32'h0230a400   |
| 4      | OR R9, R2, R5   | 32'h02513480   |
| 5      | XOR R10, R1, R4 | 32'h0240c500   |
| 6      | SLT R1, R2, R4  | 32'h02415580   |
| 7      | ADDI R12, R4, 5 | 32'h00520600   |
| 8      | BEQ R0, R0, 15  | 32'h00f00002   |
| 9      | SW R3, R1, 2    | 32'h00209181   |
| 10     | LW R13, R1, 2   | 32'h00208681   |
| 11     | SRL R16, R14, R2| 32'h00271803   |
| 12     | SLL R15, R1, R2 | 32'h00208783   |

     iverilog -o bidhan_rv32i bidhan_rv32i.v bidhan_rv32i_tb.v
     ./bidhan_rv32i 
     gtkwave rv32_i.vcd 

Simulation Output: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/6a23ad4f-e77c-440f-a78a-96fd88c27db9)




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

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/556fabaf-78ff-470a-b68b-861c222acd55)

Here we can see pre-synthesis and post-synthesis simulation result match and we are good to move forward.

 

  
