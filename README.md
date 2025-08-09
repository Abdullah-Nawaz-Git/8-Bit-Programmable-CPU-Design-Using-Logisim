# 8-Bit Programmable CPU Design Using Logisim

## Overview
This repository contains the design and implementation of an 8-bit programmable CPU developed for the CMPE263 Computer Architecture course at Qatar University (Spring 2023). The CPU supports a 16-bit wide instruction set with 10 distinct instructions and 8-bit addressable memory.

---

## Project Components

- **CPU_Excel.xlsx** — Documentation of commands and instructions.
- **CPU_Final.circ** — Logisim simulation file of the CPU architecture.

---

## CPU Features

- 8-bit CPU with 16-bit instruction width  
- 10 instructions including arithmetic, logic, data movement, branching  
- 8 General Purpose Registers (R0–R7), each 8 bits  
- 4 Status Flags: zero, negative, carry, overflow  
- 8-bit addressable memory with 16-bit data width  
- Custom 1-bit and 8-bit adders built using NAND gates  
- ALU supporting addition, subtraction, logical operations, shifts, rotates  
- Microprocessor Unit (MPU) integrating CPU, ROM, RAM with clock and reset controls  
- Instruction decoder for efficient instruction execution  

---

## Instruction Set Summary

| Instruction | Operation               | Format (bits)           | Description                   |
|-------------|------------------------|------------------------|-------------------------------|
| ADD         | Add two registers      | `0000 00dd 0000 00ss`  | Rd = Rd + Rs                  |
| SUB         | Subtract two registers | `0101` code in operation| Rd = Rd - Rs                  |
| MOV         | Move between registers | `0111` code             | Rd = Rs                      |
| AND         | Logical AND            | `1000` code             | Rd = Rd & Rs                 |
| LSL         | Logical Shift Left     | `1100` code             | Rd <<= Rs                    |
| LSR         | Logical Shift Right    | `1101` code             | Rd >>= Rs                    |
| LDI         | Load Immediate         | `0010 00dd kkkkkkkk`   | Load 8-bit immediate to Rd    |
| LDR         | Load from RAM          | `0011 00dd kkkkkkkk`   | Load memory to Rd             |
| STR         | Store to RAM           | `0100 00dd kkkkkkkk`   | Store Rd to memory            |
| BRIZ        | Branch if zero         | `0110 0001 aaaaaaaa`   | Branch if zero flag set       |
| BRIC        | Branch if carry        | `0110 0000 aaaaaaaa`   | Branch if carry flag set      |

---

## Assembly Program Example

Multiply 2 by 4:

LDI R5, 2 ; Load 2 into R5
STR R5, 0xAB ; Store R5 to memory location 0xAB
LDR R0, 0xAB ; Load memory 0xAB into R0
MOV R1, R0 ; Move R0 to R1
LSL R0, R0 ; Shift left (multiply by 2)
LSL R0, R0 ; Shift left again (multiply by 4)
ADD R0, R1 ; Add R1 to R0
STR R0, 0xAB ; Store result back in memory 0xAB


---

## Getting Started

1. Install [Logisim](http://www.cburch.com/logisim/).  
2. Open `CPU_Final.circ` in Logisim to simulate the CPU.  
3. Refer to `CPU_Excel.xlsx` for command details and instruction encoding.  
4. Use provided assembly instructions and test programs to explore CPU operations.  

---

## Conclusion

This project deepened our understanding of CPU design by constructing a working 8-bit CPU model with instruction decoding, arithmetic/logic operations, and memory management. The experience strengthened our teamwork, problem-solving, and architecture skills.
