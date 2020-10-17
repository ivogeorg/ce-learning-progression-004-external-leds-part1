# CPE 1040 - Fall 2020

## Learning Progression 004: GPIO pins and LEDs

```
  _______ ____  _____   ____  
 |__   __/ __ \|  __ \ / __ \ 
    | | | |  | | |  | | |  | |
    | | | |  | | |  | | |  | |
    | | | |__| | |__| | |__| |
    |_|  \____/|_____/ \____/ 
```                              
## 1. Rename?
1. Electricity  
2. Bottom of the stack  
3. Fundamentals of computation  
4. Computer fundamentals  

## 2. Lab kit
1. Parts for progression  

## 3. Parts
1. Fundamentals 1
   - Binary
   - Data & memory
   - Computation
   - Minimal assembler (Part 1)
2. Fundamentals 2
   - Minimal assembler (Part 2)
   - Electricity & magnetism
   - Circuits & circuit elements
   - Circuit measurements with a multimeter
3. micro:bit hardware
   - Basic LED load circuit
   - micro:bit breakout connector
   - micro:bit GPIO pins & digital/analog functions
   - Extending the 5x5 LED matrix with 2 external-LED rows for screensavers.js  


### Topics

1. Binary  
   - unsigned integers   
   - finite bit-width   
   - signed integers (derive via 1s-, then 2s-complement)  
   - IEEE 754 floating point  

2. Data & memory.  
   - memory layout  
   - addressing  
   - addressing modes  

3. Computation
   - arithmetic    
   - shifting   
   - multiplication by addition & shift  
   - challenge: multiplication of two 16-bit numbers on an 8-bit processor  

4. Minimal assembler (part 1)  
   - [MISC](https://www.google.com/search?q=misc+instruction+set)    
   - ATMEL ISA (too complex)  
   - [F-4](http://www.dakeng.com/misc.html)  
     
     The instruction set for the F-4 (fast 4), a proof-of-concept minimal instruction set CPU, is listed below.  Each instruction has several addressing modes. Note that the mnemonics are borrowed from the venerable Motorola SY6502, used in the old 8-bit Nintendo, among other machines.  There is only one "A" register or accumulator, and a program counter.

     **F-4 MISC 16 bit instruction set**
     instruction | opcode | operand | operation | clocks
     --- | --- | --- | --- | ---
     ADDi imm | 00 01 | 16 bit value | imm+(A) --> A | 3
     ADDm addr | 00 02 | 16 bit address | (addr)+(A) --> A | 4
     ADDpc | 00 04 | null operand | PC+(A) --> A | 3
     BVS addr | 00 08 | 16 bit address | (addr) --> PC if <v>=1 | 3
     LDAi imm | 00 10 | 16 bit value | imm --> A | 3
     LDAm addr | 00 20 | 16 bit address | (addr) --> A | 3
     LDApc | 00 40 | null operand | PC --> A | 3
     STAm addr | 00 80 | 16 bit address | A --> (addr) | 3
     STApc PC | 01 00 | null operand | A --> PC | 3
  
     The four instructions can be summarized as Load, Store, Add, and Branch if Overflow Set.  Each memory operation is assumed to take one clock, and ALU operations take one clock also.  ALU (Arithmetic and Logic Unit) is something of a misnomer here, since this chip can only add.  For example, "ADD addr" takes four clocks, two to fetch the instruction and operand, one to read the memory, and one more to do the addition.

5. Minimal assembler (part 2)  
   - TBD
   
6. Electricity & magnetism
   - charge, voltage, current
   - Kirchhoff's laws  
   - parallel and in-series resistors  

7. Circuits & circuit elements  
   - resistor  
   - capacitor  
   - inductor  
   - diode  
   - wires  
   - voltage/current source (battery)  
   - mechanical switches  

8. Multimeter  
   - voltage  
   - current  
   - resistance  
   - diode/continuity  

9. Basic LED circuit  
   - LED current and voltage drop  

10. Microbit breakout [guide](https://learn.sparkfun.com/tutorials/microbit-breakout-board-hookup-guide?_ga=2.103632514.348660827.1599098328-1062375953.1592240158)  
11. Microbit GPIO pins and digital/analog functions  
    - write out to drive external LED circuit
    - read in (simple resistor and LED circuits)
    - digital vs analog (binary vs continuous-level signal)
    - calibration of analog in
    - write out and read in together to close the external-circuit loop

12. Screensaver extension   
    - two extra rows for a 7x5 matrix   
    - extension of all sub-programs  


### Step 1:   

#### 1. Study

#### 2. Apply

#### 3. Present

