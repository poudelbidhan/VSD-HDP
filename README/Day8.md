## Advanced SDC constraint and Synthesis 
### Synopsys Design Constraint (SDC) 
Synopsys Design Constraints (SDC) is a widely used format for specifying design constraints in digital circuit design, particularly for timing analysis and synthesis. SDC files provide a standardized way to communicate the timing and physical constraints of a design to Electronic Design Automation (EDA) tools. Here’s a detailed overview of SDC:
#### Purpose of SDC
SDC files are used to:

1. Define Timing Constraints: Specify the timing requirements for the design to ensure it operates correctly at the desired clock frequency.
2. Set Physical Constraints: Provide physical placement and routing guidelines.
3. Guide Synthesis and Optimization: Direct synthesis tools on how to optimize the design for performance, area, and power

### Key Elements of SDC
1. Clock Definitions
Define the primary and derived clocks in the design, including their frequencies, waveforms, and relationships.

* create_clock: Defines a primary clock signal

      create_clock -period 10 [get_ports clk]
  
* create_generated_clock: Defines a clock derived from another clock.
    
      create_generated_clock -name clk_div2 -source [get_ports clk] -divide_by 2 [get_pins divider/clk_out]

2. Timing Constraints
Specify setup and hold time requirements, input and output delays, and other timing-related constraints.

* set_input_delay: Specifies the delay for signals arriving at input ports relative to a clock.

      set_input_delay -clock [get_clocks clk] 2 [get_ports data_in]
  
* set_output_delay: Specifies the delay for signals at output ports relative to a clock

      set_output_delay -clock [get_clocks clk] 2 [get_ports data_out]

3. Clock Uncertainty and Latency
Define uncertainties and latencies for clock signals to account for variations and delays.

* set_clock_uncertainty: Specifies the uncertainty (jitter) in the clock signal.

      set_clock_uncertainty 0.1 [get_clocks clk]

* set_clock_latency: Specifies the latency of the clock signal.

      set_clock_latency 1 [get_clocks clk]

4. Multicycle and False Paths
Identify paths that require multiple clock cycles or should be ignored during timing analysis.

* set_multicycle_path: Defines paths that require multiple clock cycles.

       set_multicycle_path 2 -setup -from [get_pins reg1/Q] -to [get_pins reg2/D]

* set_false_path: Defines paths that should be ignored in timing analysis

       set_false_path -from [get_ports reset] -to [get_ports data_out]

5. Maximum and Minimum Delay Constraints
Specify the maximum and minimum allowable delays for paths in the design.

* set_max_delay: Sets the maximum delay for a path

        set_max_delay 15 -from [get_ports a] -to [get_ports b]

* set_min_delay: Sets the minimum delay for a path.

        set_min_delay 5 -from [get_ports a] -to [get_ports b]

6. Load and Drive Constraints
Specify the load capacitance on outputs and the drive strength of inputs.

* set_load: Specifies the capacitive load on an output port.

      set_load 2.5 [get_ports data_out]

* set_driving_cell: Specifies the cell driving an input port.

       set_driving_cell -lib_cell INV_X1 [get_ports data_in]



   
### STA Basics
### Timing Arcs 
1. Combinational arcs: Between input and output pin of a combinational block/ cell.
2. Sequential arcs: Between the clock pin and either the input or output
3. Timing check arc: Between the clock pin and the input. (For example, the setup and hold timing arcs between the clock pin and input data pin of a Flip Flop)
4. Delay arc: Between the clock pin and the output.
5. Net arcs: Between the output pin of a cell to the input pin of another cell. (i.e., between the driver pin of a net and the load pin of that net)

### Unateness
Defines how the output changes for different types of transitions on the input.

1. Positive unate: Rising input transition causes rising output transition and falling input transition causes falling output transition.
Examples: Buffer, AND Gate, OR Gate
2. Negative unate: Rising input transition causes falling output transition and falling input transition causes rising output transition.
Examples: Inverter, NAND Gate, NOR Gate
3. Non-unate: The output transition is determined not only by the direction of an input but also on the state of the other inputs.
Examples: XOR Gate


### SDC for RISC_V

      set_units -time ns
      set period 10.000
      create_clock -name clk -period $period [get_ports {clk}]
      
      set_clock_latency -source -min 1 clk
      set_clock_latency -source -max 4 clk
      
      set clk_uncertainty_factor_setup 0.05
      set clk_uncertainty_setup [expr $period * $clk_uncertainty_factor_setup]
      set clk_uncertainty_factor_hold 0.02
      set clk_uncertainty_hold [expr $period * $clk_uncertainty_factor_hold]
      set_clock_uncertainty -setup $clk_uncertainty_setup [get_clock clk]
      set_clock_uncertainty -hold $clk_uncertainty_hold [get_clock clk]
      
      set min_input_dly_factor 0.1
      set max_input_dly_factor 0.3
      set min_input_dly [expr $period * $min_input_dly_factor]
      set max_input_dly [expr $period * $max_input_dly_factor]
      set_input_delay -clock clk -min $min_input_dly [get_ports reset]
      set_input_delay -clock clk -max $max_input_dly [get_ports reset]
      
      
      set min_tran_factor 0.01
      set max_tran_factor 0.05
      set min_tran [expr $period * $min_tran_factor]
      set max_tran [expr $period * $max_tran_factor]
      set_input_transition -max $min_tran [get_ports reset]
      set_input_transition -min $max_tran [get_ports reset] 
      
      set min_ouput_dly_factor 0.2
      set max_ouput_dly_factor 0.5
      set min_ouput_dly [expr $period * $min_ouput_dly_factor]
      set max_ouput_dly [expr $period * $max_ouput_dly_factor]
      set_output_delay -clock clk -min $min_ouput_dly [get_ports out]
      set_output_delay -clock clk -min $max_ouput_dly [get_ports out]
