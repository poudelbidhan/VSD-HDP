## Standard Cell Design Flow

Designing a Standard cell is done in 3 parts:

* Inputs - PDKs, DRC & LVS rules, Spice models, library and user-defined specs (Height,Width etc)
* Design steps - Circuit Design, Layout Design & Characterization using GUNA software. Characterization is done for Noise, Power & Timing.
* Outputs - CDL file (circuit desciption language file), GDS II, extracted spice netlist(.cir), timing, noise, power.libs function
  
### Characterization flow
The GUNA software is used for characterizing a standard cell. Cells of different strength & functionality are characterized for different PVT corners using following steps:

Read the models and tech file
Read extracted spice netlist
Read Subckt
Attach power sources
Apply input or stimulus
Apply suitable load Cap
Pass necesary simulation commands


## Designing a Custom CMOS Inverter cell
Creation of single height standard cell and plug this custom cell into a more complex design and perform it's PnR in the openlane flow. The standard cell chosen is a basic CMOS inverter and it will be plugged into the picorv32a core. More details in Nickson's Github link

#### Steps to extract spice netlist from layout (in Magic)

    extract all
    ext2spice cthresh 0 rthresh 0 #Extracting parasitic R & C
    ext2spice # Generates a spice netlist

* open the .mag Inverter layout file in magic
  

![image](https://github.com/user-attachments/assets/3ee283e8-c073-4c79-95a8-749f8d924094)

### SPICE Deck creation and SPICE Simulation 


![image](https://github.com/user-attachments/assets/347cb0bd-4f0d-45c1-a7a8-c9d1722e6358)

We will create a SPICE deck for the inverter model. SPICE deck will have the following things :

![image](https://github.com/user-attachments/assets/6812bac6-f256-432a-80b4-79e241bd9be0)

* Open Inverter spice file with ngspice
    
       ngspice sky130_inv.spice

*  For plotting the waveform use
    
        plot y vs time a 

![image](https://github.com/user-attachments/assets/e4978e22-1d32-49aa-8b12-560300375745)



plot
![image](https://github.com/user-attachments/assets/05df209c-5c74-44b7-8335-f7d1e54bd2e3)



### LEF Generation of a Standard Cell 


