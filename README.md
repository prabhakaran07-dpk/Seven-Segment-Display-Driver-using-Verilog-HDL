# Seven-Segment-Display-Driver-using-Verilog-HDL
# EXP NO: 2.A Seven-Segment Display Driver using Verilog HDL
# Aim
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

# Apparatus Required
Vivado 2023.1

# Procedure

1. Launch Vivado 2023.1
Open Vivado and create a new project.
2. Design the Verilog Code
Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.
3. Create the Testbench
Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.
4. Create the Verilog Files
Create both the design module and the testbench in the Vivado project.
5. Run Simulation
Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs 0000 to 1001 (decimal 0 to 9).
6. Observe the Waveforms
Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.
7. Save and Document Results
Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.

# Verilog Code for Seven-Segment Display
```
module bcd2sev_seg(
    input [3:0] bcd,
    output reg [6:0] seg
);
always @(*) begin
    case (bcd)
        4'd0: seg = 7'b1111110;
        4'd1: seg = 7'b0110000;
        4'd2: seg = 7'b1101101;
        4'd3: seg = 7'b1111001;
        4'd4: seg = 7'b0110011;
        4'd5: seg = 7'b1011011;
        4'd6: seg = 7'b1011111;
        4'd7: seg = 7'b1110000;
        4'd8: seg = 7'b1111111;
        4'd9: seg = 7'b1111011;
        
    endcase
end
endmodule
```
# Testbench for Seven-Segment Display
```

`timescale 1ns / 1ps
module tb_bcd2sev_seg;
reg [3:0] bcd;
wire [6:0] seg;
integer i;
bcd2sev_seg uut(bcd, seg);
initial begin
    $display("BCD  seg(abcdefg)");
    for (i=0; i<16; i=i+1) begin
        bcd = i;
        #10;
        $display("%d    %b", bcd, seg);
    end
    $finish;
end
endmodule

```

# Simulated Output

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9350b7c5-c0d7-4fe2-bc96-0bf1f9490135" />


# Conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs.

This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
