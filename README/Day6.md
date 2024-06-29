# RISC_V Design Synthesis and Gate Level Simulation 

Here, we will do the synthesis and gate-level simulation of our RISC-V RV32I design file. 

First, we copy our design verilog and testbench file to our working directory. I have placed bidhan_rv32i.v and bidhan_rv32i_tb.v files inside the synthesis folder.

 ![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/43df5a93-e3da-42da-9750-0678c02e5d8d)


 ### Functional Simulation 

     iverilog -o bidhan_rv32i bidhan_rv32i.v bidhan_rv32i_tb.v
     ./bidhan_rv32i 
     gtkwave rv32_i.vcd 

Simulation Output: 

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/6a23ad4f-e77c-440f-a78a-96fd88c27db9)




### Synthesis 

Here we do the synthesis of our design file with yosys. 
You can do that either by running following commands one at a time. 

    read_verilog bidhan_rv32i.v
    synth -top rv32i
    dfflibmap -liberty /home/bidhan/project/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    proc; opt
    abc -liberty /home/bidhan/project/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    clean
    flatten
    write_verilog -noattr bidhan_rv32i_synth.v

Or, you can create a ``` .sh ``` file with all the commands inside it and run the script once. 

    yosys
    script synthesis.sh

  In the end, we should successfully get the synthesized file named bidhan_rv32i_synth.v
  

### Gate Level Simulation 

 We do the gate-level simulation to verify the logical correctness of the design after synthesizing the design. 

 

  
