## STATIC TIMING ANALYSIS RV32i

    read_liberty ./sky130_fd_sc_hd__tt_025C_1v80.lib
    read_verilog ./verilogfiles/rv32i_synth.v <Path to synthesized netlist file>
    link_design rv32i
    current_design
    read_sdc ../sky130RTLDesignAndSynthesisWorkshop/sdc/riscv_core_synthesis.sdc
    create_clock -name clk -period 10.0000 [get_ports {clk}]
    check_setup -verbose -unconstrained_endpoints
    report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4}


Result_reports : 

![image](https://github.com/user-attachments/assets/d4cfc38c-73f1-4e42-b623-a62e5189f091)

![image](https://github.com/user-attachments/assets/3db3b56f-686e-4160-8bd3-748662979e19)
i
