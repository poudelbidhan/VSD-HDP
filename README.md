# VSD-Hardware Design Program
## Tool Installation 
### System Information
1. OS: Ubuntu 22.04
2. RAM: 8 GB
3. Storage: 100 GB
4. Processor: 4 Core



### Yosys: Synthesis

```sh
sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make # If make is not installed please install it
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make 
sudo make install
```
![Screenshot from 2024-06-06 20-50-06](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/cdb64531-ef3f-4d21-876b-dc78a66a2c56)

### iVerilog

```
sudo apt install iverilog
iverilog -v

```



![Screenshot from 2024-06-06 21-19-24](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/fe6a9b25-1ce5-4b62-a794-a58204a7db8f)



### GTKWave
```
sudo apt install gtkwave
gtkwave
```
![Screenshot from 2024-06-06 21-31-09](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/3591863c-a35f-4237-ba05-f542f9ca4217)


## Day 1: Introduction to Verilog RTL Design and Synthesis
### Functional Simulation of RTL Design Using iverilog and rtkwave

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


### Logic Synthesis using Yosys
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




## Day 2: Timing libs, Hierarchical vs. Flat Synthesis, Flip-Flop coding styles
    
   
   

