# CPE 1040 - Fall 2020

This is learning progression 003 for the Fall 2020 installment of the course CPE 1040: Introduction to Computer Engineering at MSU Denver.

Table of Contents
=================


## Learning Progression 004: External LEDs (Part 1 - Fundamentals of computing I)


### Step 1: Binary   
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

##### Unsigned integers

```javascript
// Example 1.1.1

// toUnsignedBinaryString
//
// 3 : 2 = 1.5  --> 1     Q > floor(Q)       11
// 1 : 2 = 0.5  --> 1
//
// 2 : 2 = 1.0  --> 0     Q == floor(Q)      10
// 1 : 2 = 0.5  --> 1
function toUnsignedBinaryString(dec : number) : string {
    let bin_array : number[] = []
    let quotient : number = dec
    let no_fraction : number

    while (true) {
        quotient /= 2
        no_fraction = Math.floor(quotient)
        if (quotient > no_fraction)
            bin_array.insertAt(0, 1)
        else
            bin_array.insertAt(0, 0)
        if (no_fraction == 0) break
    }

    return '0b' + 
           bin_array.map(
               (value: number, index: number) => 
               { return value.toString(); }
               ).join('')
}
```

##### Finite bit width   

##### Signed integers

Present  

##### IEEE 754 floating point  

#### 2. Apply
[[toc](#table-of-contents)]

(Challenge) Derive via 1s-, then 2s-complement  


#### 3. Present
[[toc](#table-of-contents)]

### Step 2: Data & memory  
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

   - memory layout  
   - addressing  
   - addressing modes  

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 3: Computation
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

   - arithmetic    
   - shifting   
   - multiplication by addition & shift  
   - challenge: multiplication of two 16-bit numbers on an 8-bit processor  

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

### Step 4: Minimal assembler (part 1)  
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

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

#### 2. Apply
[[toc](#table-of-contents)]

#### 3. Present
[[toc](#table-of-contents)]

