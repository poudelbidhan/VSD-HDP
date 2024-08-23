# RTL to GDS flow of RISC_V design on Openlane Flow 


First I have a Verilog design file for the PicoRV32 Risc_v based processor. I want to implement this rtl and tape out my design in OpenLane flow.


## Step 1: Openlane Installation 
* Install Docker on your Linux machine.
  
    Installation Guide: https://docs.docker.com/engine/install/ubuntu/

  * Make Docker Available Without a Root
  * Clone OpenLane GitHub repo and make the files
 
    
        git clone --depth 1 https://github.com/The-OpenROAD-Project/OpenLane.git
        cd OpenLane/
        make
        make test # This a ~5 minute test that verifies that the flow and the pdk were properly installed


    * Run a test to verify everything has been installed and openlane is working as expected.
   
      ![image](https://github.com/user-attachments/assets/a5eb82f3-8d96-445f-a650-9318520e067f)

## Step 2: Design Preparation 
* To add a new design run the command

      ./flow.tcl -design risc_v -init_design_config -add_to_designs -cofig_file config.tcl

It will create a new dir under designs folder named risc_v and it will generate the new `config.tcl` file as well. 


  ![image](https://github.com/user-attachments/assets/b38a3375-a19b-435d-b60a-d3ac956892b2)


* Now, populate the risc_v design verilog file in src folder.
* 
    
