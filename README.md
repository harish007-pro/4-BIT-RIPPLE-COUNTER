# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**
1.Increment count on each positive edge of the clock.
2.Reset count to zero when it reaches 15. 
3.Generate clock signal (clk).
4.Instantiate the RippleCounter module.
5.Conduct functional testing by displaying the count at each clock cycle for 16 cycles.

**PROGRAM**
 Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.
```
 Developed by: HARISH G
 RegisterNumber:212224110020
```
```
module ripple_counter_4bit (
    input clk,         // Clock input
    input reset,       // Asynchronous reset
    output [3:0] q     // 4-bit counter output
);

    wire clk1, clk2, clk3;

    // First flip-flop toggles with main clock
    T_FF tff0 (.clk(clk), .reset(reset), .q(q[0]));

    // Subsequent flip-flops toggle with output of previous FF
    T_FF tff1 (.clk(q[0]), .reset(reset), .q(q[1]));
    T_FF tff2 (.clk(q[1]), .reset(reset), .q(q[2]));
    T_FF tff3 (.clk(q[2]), .reset(reset), .q(q[3]));

endmodule

// T Flip-Flop module
module T_FF (
    input clk,
    input reset,
    output reg q
);
    always @(posedge clk or posedge reset)
    begin
        if (reset)
            q <= 0;
        else
            q <= ~q;
    end
endmodule
```


**RTL LOGIC FOR 4 Bit Ripple Counter**
![398323659-d91f7f5c-7320-4e66-9822-c76178538294](https://github.com/user-attachments/assets/36253941-f06c-4058-8d27-40596bd78b90)

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
![398323747-a7868c4c-fa53-485f-97c6-a0029262da49](https://github.com/user-attachments/assets/d2b1a2ca-e84a-4f0d-96dd-1cac4bbe602a)

**RESULTS**
Thus the program executed sucesssfully.
