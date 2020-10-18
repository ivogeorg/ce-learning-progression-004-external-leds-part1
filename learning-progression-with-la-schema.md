# CPE 1040 - Fall 2020

This is learning progression 004 for the Fall 2020 installment of the course CPE 1040: Introduction to Computer Engineering at MSU Denver.

Table of Contents
=================

* [CPE 1040 \- Fall 2020](#cpe-1040---fall-2020)
* [Table of Contents](#table-of-contents)
  * [Learning Progression 004: External LEDs (Part 1 \- Fundamentals of computing I)](#learning-progression-004-external-leds-part-1---fundamentals-of-computing-i)
    * [Step 1: Binary](#step-1-binary)
      * [1\. Study](#1-study)
        * [Unsigned integers](#unsigned-integers)
        * [Finite bit width](#finite-bit-width)
        * [Signed integers](#signed-integers)
        * [IEEE 754 floating point](#ieee-754-floating-point)
      * [2\. Apply](#2-apply)
      * [3\. Present](#3-present)
    * [Step 2: Data &amp; memory](#step-2-data--memory)
      * [1\. Study](#1-study-1)
        * [Memory layout](#memory-layout)
        * [Addressing](#addressing)
        * [Addressing modes](#addressing-modes)
      * [2\. Apply](#2-apply-1)
      * [3\. Present](#3-present-1)
    * [Step 3: Computation](#step-3-computation)
      * [1\. Study](#1-study-2)
        * [Addition](#addition)
        * [Shifting](#shifting)
        * [Multiplication](#multiplication)
      * [2\. Apply](#2-apply-2)
      * [3\. Present](#3-present-2)
    * [Step 4: Minimal assembly (part 1)](#step-4-minimal-assembly-part-1)
      * [1\. Study](#1-study-3)
        * [Central processing unit (CPU)](#central-processing-unit-cpu)
        * [Instruction set](#instruction-set)
        * [Minimal instruction set CPU](#minimal-instruction-set-cpu)
        * [micro:bit hex files](#microbit-hex-files)
      * [2\. Apply](#2-apply-3)
      * [3\. Present](#3-present-3)


## Learning Progression 004: External LEDs (Part 1 - Fundamentals of computing I)

This progression introduces fundamentals of computing, including the binary system of data representation as well as the basics of memory and processing. We introduce assembly language in the context of a minimal instruction set processor. This is the lowest level of the software stack, where user programs are translated into machine code, executed step-by-step by the processor. This is also the level of computing which directly correpsonds to the simplest theoretical models of a computer. We also introduce the input-output capabilities of the micro:bit and build an external circuit to serve as an extension to the built-in 5x5 LED matrix to run our Screensavers program on.

### Step 1: Binary   
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

##### Unsigned integers

`[<lernact-rd>]`

```javascript
// Example 1.1.1

/**
 * Converts an unsigned decimal integer to a binary bit pattern string.
 * 
 *           Quotient     Remainder   Condition          Result
 *   3 : 2 = 1.5  ------> 1           Q > floor(Q)       11
 *   1 : 2 = 0.5  ------> 1           floor(Q) == 0 
 *
 *   2 : 2 = 1.0  ------> 0           Q == floor(Q)      10
 *   1 : 2 = 0.5  ------> 1           floor(Q) == 0
 *
 * @param dec unsigned decimal integer
 */
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

1. `[<lernact-prac>]`  
2. `[<lernact-prac>]`  
3. `[<lernact-prac>]`**[Optional challenge, max 10 extra step points]** Derive signed integers via 1s-, then 2s-complement  


#### 3. Present
[[toc](#table-of-contents)]


### Step 2: Data & memory  
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

##### Memory layout  

##### Addressing  

##### Addressing modes  

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`  
2. `[<lernact-prac>]`  
3. `[<lernact-prac>]`  

#### 3. Present
[[toc](#table-of-contents)]


### Step 3: Computation
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

##### Addition

##### Shifting   

##### Multiplication

Addition & shift  

#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`  
2. `[<lernact-prac>]`  
3. `[<lernact-prac>]`**[Optional challenge, max 10 extra step points]** Multiplication of two 16-bit numbers on an 8-bit processor  

#### 3. Present
[[toc](#table-of-contents)]


### Step 4: Minimal assembly (part 1)  
[[toc](#table-of-contents)]

#### 1. Study
[[toc](#table-of-contents)]

##### Central processing unit (CPU)

##### Instruction set

##### Minimal instruction set CPU

[F-4 MISC](http://www.dakeng.com/misc.html)  
     
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

##### micro:bit hex files


#### 2. Apply
[[toc](#table-of-contents)]

1. `[<lernact-prac>]`Reading program lines in binary.  
2. `[<lernact-prac>]`Clock cycles for a program.    
3. `[<lernact-prac>]`**[Optional challenge, max 10 extra step points]** Write a function in F-4 MISC assembly.  

#### 3. Present
[[toc](#table-of-contents)]

