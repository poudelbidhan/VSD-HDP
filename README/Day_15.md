
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
* Created a `.sdc` file and placed in the same directory.

### Step 3: Running the design 
* After creating all the needed source files and sdc files.  Run the following Command.


     openlane ~/my_designs/risc_v/config.json


  * OpenLane2 will start the flow. It will take some time depending upon the complexity of the design and design constraints we havfe set.
  * Once the flow is complete, you can see this. 
![image](https://github.com/user-attachments/assets/abd46a0e-9810-4630-aeeb-82f835da9f1a)




### Checking the Results 

###  Viewing Layout on Klayout 

![image](https://github.com/user-attachments/assets/dc3470ca-5422-4930-b970-79dd5c24ec5e)

### Run Directory 
The tool will create run directoy when we run the openlane. 
![image](https://github.com/user-attachments/assets/b780f597-fe37-4cbf-8ecb-9b98a7d2313a)

![image](https://github.com/user-attachments/assets/508752c8-7632-4521-a546-a842f325442d)


  
