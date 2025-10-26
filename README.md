# 4-BIT-RIPPLE-COUNTER

AIM:

To implement 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

SOFTWARE REQUIRED:

Quartus prime

THEORY

4 Bit Ripple Counter

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

<img width="602" height="320" alt="image" src="https://github.com/user-attachments/assets/b64da624-f2d8-4eac-944f-1bde9b510255" />


In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

<img width="356" height="271" alt="image" src="https://github.com/user-attachments/assets/ceef0cd3-36bd-4daa-a3dc-c253e0fe8577" />


<img width="254" height="198" alt="image" src="https://github.com/user-attachments/assets/1ac32e1a-1d1a-4ff3-82c4-201c4b020d75" />


Procedure

1.Increment count on each positive edge of the clock. 2.Reset count to zero when it reaches 15. 3.Generate clock signal (clk). 4.Instantiate the RippleCounter module. 5.Conduct functional testing by displaying the count at each clock cycle for 16 cycles.

PROGRAM

 Developed by: ROSHAN V
 RegisterNumber: 25004228
module RippleCounter(
   input wire clk,  // Clock input
   output reg [3:0] count // 4-bit counter output
);

// Counter logic
always @(posedge clk) begin
   if (count == 4'b1111) // Reset when count reaches 15
       count <= 4'b0000;
   else
       count <= count + 1; // Increment count
end

endmodule

// Testbench
module RippleCounter_tb;

// Inputs
reg clk;

// Outputs
wire [3:0] count;

// Instantiate the counter
RippleCounter uut(
   .clk(clk),
   .count(count)
);

// Clock generation
initial begin
   clk = 0;
   forever #5 clk = ~clk; // Toggle clock every 5 time units
end

// Stimulus
initial begin
   // Wait for a few clock cycles
   #10;
   
   // Display header
   $display("Time | Count");
   $display("-----------------");
   
   // Functional table testing
   // Increment count 16 times and display the count
   repeat (16) begin
       #5; // Wait for one clock cycle
       $display("%4d | %b", $time, count);
   end
   
   // End simulation
   $finish;
end

endmodule
RTL LOGIC FOR 4 Bit Ripple Counter

<img width="756" height="410" alt="image" src="https://github.com/user-attachments/assets/22ba0b7d-4c56-4b99-a85f-07f2edec8256" />


TIMING DIGRAMS FOR 4 Bit Ripple Counter

<img width="1098" height="362" alt="image" src="https://github.com/user-attachments/assets/656c5b5a-5edb-40bd-b5b1-865349b0a827" />


RESULTS Thus the program executed succesfully.


