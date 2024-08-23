
# RTl to GDS in OpenLane2 flow 

First I have a Verilog design file for the PicoRV32 Risc_v based processor. I want to implement this rtl and tape out my design in OpenLane2 flow. 



### Step 1: OpenLane2 Installation 

* Nix based installation :
  
  The installation guide can be found here: https://openlane2.readthedocs.io/en/latest/getting_started/common/nix_installation/installation_linux.html

* After Nix installation simple clone the openlane2 git repo

    git clone https://github.com/efabless/openlane2

* Go inside the openlane2 dir and run `nix-shell'. It will take some time to unpack the binaries.
* For a quick installation test, you can run `openlane --smoke-test `. 
