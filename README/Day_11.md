## Floorplan considerations, Placement, Library Cells

### Floorplan considerations
1. Utilization factor and aspect ratio

* Define W, H of core and die
    Utilization Factor = (Area occupied by netlist)/(Total area of the core)
    Usually we aim for 50-60 % Utilization Factor
* Aspect Ratio = Height/ Width
  
2. Define locations of pre-placed cells (macros and IPs ?)

* IPs/ blocks have user-defined locations and hence placed before automated PnR and are called as pre-placed cells
* Automated PnR tools places the remaining logical cells in the design onto the chip
3. Decaps
* Decouples the circuit from the VDD rail
* Reduce Zpdn for the required frequencies of operation
* Serve as a charge reservoir for the switching current demands that the VDD rail cannot satisfy.
* Surround pre-placed cells with Decaps to compensate for the switching current demands (di/dt)

  
4. Power Planning

* SSN
    L*di/dt
    Discharging : Ground bounce
    Charging : Voltage Droop
  
    Solution: Reduce the Vdd/ Vss parasitics ->
    Power grid
    Multiple VDD, VSS pins/ balls
  
5. Pin Placement

* Usually: East -> West, North -> South, {East, North} -> {West, South}
* Pin ordering is random (unless we specify explicitly ?)
* Front-end to Back-End team communication/ handshaking needed for optimal pin placement
* CLK ports/ pins are usually bigger to reduce the clk net resistance
* Logical Cell placement blockage - so that no cells are placed by the PnR tool inside the IP blocks/ macro area.

### Lab: Run floorplan using OpenLANE and review the layout in Magic
* To run the floorplan creation, execute the following command from the OpenLANE shell: `run_floorplan`


![image](https://github.com/user-attachments/assets/2761a405-1874-4296-b3bd-6112e05b2e81)

* To view the floorplan in Magic

  
      cd to the floorplan results directory for the current run: openlane/designs/<design-name>/runs/<time-stamp>/results/floorplan
       magic -T $PDK_ROOT/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read ./picorv32a.floorplan.def &
![image](https://github.com/user-attachments/assets/b6f4dc2d-1408-445b-a752-f50e04b43cb7)


![image](https://github.com/user-attachments/assets/ba411018-c0a9-451e-8ee9-beed24e41c17)
