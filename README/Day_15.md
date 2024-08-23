
# RTl to GDS in OpenLane2 flow 

First I have a Verilog design file for the PicoRV32 Risc_v based processor. I want to implement this rtl and tape out my design in OpenLane2 flow. 



### Step 1: OpenLane2 Installation 

* Nix based installation :
  
  The installation guide can be found here: https://openlane2.readthedocs.io/en/latest/getting_started/common/nix_installation/installation_linux.html

* After Nix installation simple clone the openlane2 git repo

    git clone https://github.com/efabless/openlane2

* Go inside the openlane2 dir and run `nix-shell'. It will take some time to unpack the binaries.
* For a quick installation test, you can run `openlane --smoke-test `. 

![image](https://github.com/user-attachments/assets/1b4f3c67-9a2c-4f3a-b911-d2bfac75dac8)

### Step2 :  Design Preparation 

After successfully installing openlane2, we must create our design directory, place library, and other required files. 

* Create `design` dir and under this directory we place our `.v` design file.
* I created a new dir `design` under this `riscv` and under this `src` where I copied my verilog design file.
  
![image](https://github.com/user-attachments/assets/380fd66e-d2f6-4cea-9755-9366c113a376)
