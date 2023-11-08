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
Connect the supply (+5V) to the circuit. Switch ON the main switch. If the output is 1, then the bulb glows.



### PROGRAM 
```
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: Ranjan K
RegisterNumber: 212222230116
```

## UPCOUNTER:
```
module uc(clk,A);
input clk;
output reg [3:0]A;
always@(posedge clk)
begin
A[3]=((A[2]&A[1])&A[0])^A[3];
A[2]=(A[1]&A[0])^A[2];
A[1]=(A[0]^A[1]);
A[0]=1^A[0];
end
endmodule
```

## DOWNCOUNTER:
```
module dc(clk,A);
input clk;
output reg [3:0]A;
always @(posedge clk)
begin
A[3]=((~A[2])&(~A[1])&(~A[0]))^A[3];
A[2]=((~A[1])&(~A[0]))^A[2];
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule

```

### RTL LOGIC UP COUNTER AND DOWN COUNTER  
# UPCOUNTER:
![245136627-0a4b5a96-c4d0-4a3d-a501-4d57d46f37b8](https://github.com/Praveenkumar2004-dev/Exp-7-Synchornous-counters-/assets/119559827/1214d605-8b18-4b2e-892e-278e7701c19c)



# DOWNCOUNTER:
![245136699-692e0239-810e-40fe-85d4-8753d18abb66](https://github.com/Praveenkumar2004-dev/Exp-7-Synchornous-counters-/assets/119559827/69375c5b-2e44-46ba-b425-14b6bda31256)




### TIMING DIGRAMS FOR COUNTER  
# UPCOUNTER:
![245136866-97556c87-e03f-4dc5-b1a5-e9c7cfe05365](https://github.com/Praveenkumar2004-dev/Exp-7-Synchornous-counters-/assets/119559827/01c2090c-f034-4b7e-a3c9-eba2d978a67e)



# DOWNCOUNTER:
![245136920-f4328c29-280a-4d61-a943-c65419b9530e](https://github.com/Praveenkumar2004-dev/Exp-7-Synchornous-counters-/assets/119559827/3b003fc5-ef3a-4900-8c97-6f9271283481)




### TRUTH TABLE 
# Upcounter:
![truth ex06 up](https://github.com/Praveenkumar2004-dev/Exp-7-Synchornous-counters-/assets/119559827/e73019ba-ed43-4461-8ca6-c5f5711b5c2c)


# Downcounter:
![truth06down](https://github.com/Praveenkumar2004-dev/Exp-7-Synchornous-counters-/assets/119559827/cd7c6d08-5c82-468d-aae5-eeb56cef3b55)



### RESULTS:
Thus,The 4-bit up and down counter is implemented successfully.
