
## Integrating VSD Inverter Cell into the Openlane Flow 


1. Copy the lef and .lib files of the custom inverter into designs/picorv32a/src directory.


![image](https://github.com/user-attachments/assets/d45d5cfa-f341-42d1-a27b-2171fe33ab36)



3. Editing the config.tcl to change the lib files and add the extra lef file into the original flow.

![image](https://github.com/user-attachments/assets/599df242-6712-4b4d-b6c8-b61069620b1f)


### Synthesis : 


![image](https://github.com/user-attachments/assets/076cbb8f-24fd-4c48-adfc-3e19b6cb6aa5)


![image](https://github.com/user-attachments/assets/76806820-1cc1-42da-b7f8-f0d1005bdade)



again we optimize the delay and area using following env variables: 

prep -design picorv32a -tag 05-08_16-23 -overwrite

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

echo $::env(SYNTH_STRATEGY)
set ::env(SYNTH_STRATEGY) "DELAY 3"
echo $::env(SYNTH_BUFFERING)
echo $::env(SYNTH_SIZING)
set ::env(SYNTH_SIZING) 1
echo $::env(SYNTH_DRIVING_CELL)

run_synthesis

