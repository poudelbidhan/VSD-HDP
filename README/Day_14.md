
## Integrating VSD Inverter Cell into the Openlane Flow 


1. Copy the lef and .lib files of the custom inverter into designs/picorv32a/src directory.

        cp sky130_vsdinv.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src
        cp sky130_fd_sc_hd__* /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src
   

![image](https://github.com/user-attachments/assets/d45d5cfa-f341-42d1-a27b-2171fe33ab36)



3. Editing the config.tcl to change the lib files and add the extra lef file into the original flow.

       set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
       set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
       set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
       set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
       set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]

![image](https://github.com/user-attachments/assets/599df242-6712-4b4d-b6c8-b61069620b1f)


### Synthesis : 

      cd Desktop/work/tools/openlane_working_dir/openlane
      docker
      ./flow.tcl -interactive
      package require openlane 0.9
      prep -design picorv32a
      set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
      add_lefs -src $lefs
      run_synthesis


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

![image](https://github.com/user-attachments/assets/d6c6d997-efdc-46e8-ae3f-63762da4a75f)




### FloorPlanning 

    init_floorplan
    place_io
    tap_decap_or


![image](https://github.com/user-attachments/assets/cfbbd61c-a58c-4f87-82d2-d11407a13d5e)


### Placement 

  `run_placement`

![image](https://github.com/user-attachments/assets/52b54fc0-8ecf-469b-8b58-5b2a84f11a26)

Load the placement.def file in magic:

`cd /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/05-06_16-23/results/placement`

`magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &`


The placement.def file displayed on magic:

![225767544-e2429f9c-7b62-4904-bc58-92876094389e](https://github.com/user-attachments/assets/c6b359b6-246d-4992-9b0d-5dcc10637168)



