SYNCHRONOUS-UP-COUNTER
AIM:

To implement 4 bit synchronous up counter and validate functionality.

SOFTWARE REQUIRED:

Quartus prime

THEORY

4 bit synchronous UP Counter

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

Each flip-flop in this circuit will be clocked at exactly the same time. The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.” Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse. Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time. The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed. However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

Procedure

Understand the Counter Behavior Inputs:
clk: Clock signal. reset: Resets the counter to 0. Output:

count: 4-bit binary value representing the current count. Behavior:

On the rising edge of the clock: If reset = 1, the counter resets to 0. If reset = 0, the counter increments by 1. After reaching 1111 (15 in decimal), it wraps around to 0000.

PROGRAM
```
module Co_ud (
    input  wire clk,       // clock input
    input  wire rst,       // synchronous reset
	 input  wire d,
    output reg  [2:0] q   // 3-bit counter output
);

initial begin
     q <= 3'b0000;
	 end

always @(posedge clk) 
begin
q <= 3'b000;
    if (rst) 
        q <= 3'b000;       // reset counter to 0
    else if(d)
        q <= q + 1;        // increment counter
		  else
		  q <= q - 1;
end

endmodule
```

Developed by:KAVIRAJ.P
RegisterNumber:25017431

RTL LOGIC UP COUNTER
[RTL.pdf](https://github.com/user-attachments/files/24120752/RTL.pdf)

TIMING DIAGRAM FOR IP COUNTER
[wave img.bmp](https://github.com/user-attachments/files/24120769/wave.img.bmp)

RESULTS

The implementation of 4 bit synchronous up counter and validate functionality.
