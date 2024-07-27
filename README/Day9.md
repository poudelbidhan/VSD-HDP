## PVT Corner Analysis (Post-Synthesis Timing) of the RISC-V CPU Design

The STA checks are performed across all the corners to confirm the design meets the target timing requirements.

The following TCL script is used for the STA: 

  
    puts "=============Executing STA TCL File =================";
    puts "=====================================================";
    
    # Read library files --------------------------------------
    
    set list_of_lib_files(1) "sky130_fd_sc_hd__tt_025C_1v80.lib"
    
    set list_of_lib_files(2) "sky130_fd_sc_hd__ff_100C_1v65.lib"
    
    set list_of_lib_files(3) "sky130_fd_sc_hd__ff_100C_1v95.lib"
    
    set list_of_lib_files(4) "sky130_fd_sc_hd__ff_n40C_1v56.lib"
    
    set list_of_lib_files(5) "sky130_fd_sc_hd__ff_n40C_1v65.lib"
    
    set list_of_lib_files(6) "sky130_fd_sc_hd__ff_n40C_1v76.lib"
    
    set list_of_lib_files(7) "sky130_fd_sc_hd__ss_100C_1v40.lib"
    
    set list_of_lib_files(8) "sky130_fd_sc_hd__ss_100C_1v60.lib"
    
    set list_of_lib_files(9) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
    
    set list_of_lib_files(10) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
    
    set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
    
    set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
    
    set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v76.lib"
    
    # Load Liberty File --------------------------------------
    
    for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {
    
    #path to liberty lib
    
    read_liberty /home/bidhan/project/sky130RTLDesignAndSynthesisWorkshop/pvt_corners/$list_of_lib_files($i)
    
    read_verilog /home/bidhan/project/risc_v/synthesis/bidhan_rv32i_synth.v
    
    link_design rv32i
    
    current_design
    
    #create_clock -name clk_5m -period 10 {clk_5m}
    
    set period 5
    
    create_clock -period $period [get_ports clk]
    
    # Timing constraints --------------------------------------
    
    set clk_period_factor .2
    
    set delay [expr $period * $clk_period_factor]
    
    #set_input_delay -clock clk_5m 1 {din wr_en rx rdy_clr}
    
    #set_output_delay -clock clk_5m 3 {dout rdy tx tx_busy}
    
    set_input_transition .1 [all_inputs]
    
    #current_design gcd_sky130hd.sdc
    
    check_setup -verbose
    
    # Report - output  --------------------------------------
    
    report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4} > ./sta_output/min_max_$list_of_lib_files($i).txt
    
    exec echo "$list_of_lib_files($i)" >> ./sta_output/sta_worst_slack.txt
    
    report_worst_slack >> ./sta_output/sta_worst_slack.txt
    
    exec echo "$list_of_lib_files($i)" >> ./sta_output/sta_tns.txt
    
    report_tns >> ./sta_output/sta_tns.txt
    
    exec echo "$list_of_lib_files($i)" >> ./sta_output/sta_wns.txt
    
    report_wns >> ./sta_output/sta_wns.txt
    
    #report_checks -path_delay min_max -digits {4} >> ./sta_output/sta_max_min_slack_report.txt
    
    #exec echo "$list_of_lib_files($i)" >> ./sta_output/sta_max_min_slack_report.txt
    
    #report_checks min_max -digits {4} >> ./sta_output/sta_max_min_slack_report.txt
    
    puts "~~~~~~~~~~~~~~~~Execution SUCCESS~~~~~~~~~~~~~~~";
    
    }

## Generated Reports 
![image](https://github.com/user-attachments/assets/c4986b2d-3895-4e09-b345-414210d18215)




## Worst Negative Slack (WNS) Plot 

![output (1)](https://github.com/user-attachments/assets/fc3b2b7d-fbd9-40a4-92a1-abbeb5337756)


## Total Negative Slac (TNS) Plot

![output (2)](https://github.com/user-attachments/assets/e77dbb70-8fd6-4eea-9928-3507c55e4dec)





