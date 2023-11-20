# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



 
 

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

 
 

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
1.Create a new project in QuartusII software. 2.Name the project as uc for upcounter and dc for down counter. 3.Create a new verilog hdl file in the project file. 4.Name the module as dc and uc for down counter and up counter. 5.Within the module declare input and output variables. 6.Create a loop using if-else with condition parameter as reset value. 7.End the loop. 8.End the module.
### PROGRAM 
### UP COUNTER:
```
/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: HARI PRASATH S  
RegisterNumber: 212222240034
*/
module Counters(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
	A[3]=(((A[0])&(A[1])&(A[2]))^A[3]);
	A[2]=(((A[0])&(A[1]))^A[2]);
	A[1]=(A[0])^A[1];
	A[0]=A[0]^1;
end
endmodule
```
### DOWN COUNTER:
```/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: HARI PRASATH S  
RegisterNumber: 212222240034
*/
module dCounters(clk,A);
input clk;
output reg [3:0]A;
always@(posedge clk)
begin
	A[3]=(((~A[0])&(~A[1])&(~A[2]))^A[3]);
	A[2]=(((~A[0])&(~A[1]))^A[2]);
	A[1]=(~A[0])^A[1];
	A[0]=(~A[0])^1;
end
endmodule
```
### RTL LOGIC UP COUNTER AND DOWN COUNTER  
### UP COUNTER
![280440940-2c7495ec-6778-4ce9-acce-32704b5eca9a](https://github.com/hariprasath5106/Exp-7-Synchornous-counters-/assets/111515488/79923d1c-6591-4135-901f-839c3ce361b4)
### DOWN COUNTER  
![280440961-7ce0bbd1-98a4-45f2-8b5a-306c1a8af9e5](https://github.com/hariprasath5106/Exp-7-Synchornous-counters-/assets/111515488/9d32fd82-d728-4407-990f-4ad00aeaa752)
### TIMING DIGRAMS FOR COUNTER  
## UP COUNTER:
![280441041-07ae8d5f-949a-4974-bec9-eaacb0892515](https://github.com/hariprasath5106/Exp-7-Synchornous-counters-/assets/111515488/d7458286-af7b-4dd1-994d-b89108c21389)
## DOWN COUNTER
![280441079-82d5d097-7feb-45df-827e-09e2fa796de0](https://github.com/hariprasath5106/Exp-7-Synchornous-counters-/assets/111515488/27925e67-3309-4440-b16d-d40f91aa6baf)

### TRUTH TABLE 
## UP COUNTER:
![280441131-b2a4f8f2-cbb4-45a9-9159-bd614eb58a03](https://github.com/hariprasath5106/Exp-7-Synchornous-counters-/assets/111515488/e46ed7e4-f590-438d-8afc-11f3460b804d)
## DOWN COUNTER:
![280441119-e537371a-3a5d-4f5a-81bd-ba1b72e58b4e](https://github.com/hariprasath5106/Exp-7-Synchornous-counters-/assets/111515488/01481c02-487f-4a18-a1f0-b8b389577c9c)
### RESULTS 
Thus Synchornous counters up counter and down counter circuit are studied and the truth table for different logic gates are verified
