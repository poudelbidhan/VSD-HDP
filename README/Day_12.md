
## Placement and Routing 

1. Bind netlist with physical cells

* Library files
    * Shape, dimension info, power & timing/ delay info
    * Various flavors of all available std cells
2. Placement

* The location of pre-placed cells are fixed and PnR tools will not place any cells inside that area.
* Initial global placement based on the input, output pins to reduce wire lengths

  
3. Optimize placement

* Ensure that Signal Integrity is maintained
    * Estimate the wire length and capacitance and insert repeaters/ buffers
    * MaxTrans delay/ signal slew
3. Congestion aware placement using RePlAce followed by detailed placement using OpenDP
* Global placement: HPWL (Half-Parameter Wire Length) based

###  Lab: Run placement
The `run_placement` command runs the global placement followed by detailed placement.

![image](https://github.com/user-attachments/assets/5dc8f9d1-9569-4d12-aaf3-54294112e485) 

* Layout after Placement 


![image](https://github.com/user-attachments/assets/dc895d10-c332-4733-a083-405ff21552b7)

![image](https://github.com/user-attachments/assets/733b50bf-4bd9-4a98-be27-b7cbdab94c85)
