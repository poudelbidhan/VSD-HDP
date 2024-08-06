## Familiarization with OpenLane Flow 


### Design Preparation Setup 

The commands to start an interactive session and run the synthesis of the picorv32a example design are given below:


      ./flow.tcl -interactive
      package require openlane 0.9
      prep -design picorv32a
      run_synthesis




![image](https://github.com/user-attachments/assets/6e722854-dcce-4b6d-9001-7951c2112bd9)

### Synthesis Result : 


![image](https://github.com/user-attachments/assets/bbd3b00c-3883-4f5f-8eab-b6dc680c9287)


### Synthesis Statistics 

#### Flop Ratio

            Flop Ratio = (Total no. of Flops/ Total no. of cells in the design)
                       = 1613/ 14876
                       = 10.843%
