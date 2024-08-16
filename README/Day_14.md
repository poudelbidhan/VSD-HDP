
## Integrating VSD Inverter Cell into the Openlane Flow 


1. Copy the lef and .lib files of the custom inverter into designs/picorv32a/src directory.


![image](https://github.com/user-attachments/assets/d45d5cfa-f341-42d1-a27b-2171fe33ab36)



3. Editing the config.tcl to change the lib files and add the extra lef file into the original flow.

set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
