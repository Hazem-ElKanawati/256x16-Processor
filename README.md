# 16-bit Processor in VHDL

## Overview

This project implements a simple **16-bit processor architecture** using **VHDL**, following a modular RTL design approach. The processor supports a basic instruction set and executes instructions through a **Fetch–Decode–Execute cycle**.

The design demonstrates key computer architecture concepts including datapath organization, control logic, memory interfacing, and ALU operations.

---

## Architecture

### Main Components

* **Program Counter (PC)** – Holds the address of the current instruction
* **Instruction Memory (ROM)** – Stores 16-bit instructions
* **Control Unit** – Decodes instructions and generates control signals
* **Register File (16×4)** – General-purpose registers
* **Data Memory (256×16)** – Stores data for load/store operations
* **Arithmetic Logic Unit (ALU)** – Performs arithmetic and logical operations
* **Multiplexers (MUXes)** – Control data routing within the datapath
* **INPR / OUTR Registers** – Handle input/output operations

---

## Design Methodology

### Modular RTL Design

Each hardware block is implemented as an independent VHDL module:

* Improves readability and maintainability
* Enables independent testing of components
* Simplifies system integration

### Key Features

* Datapath and control separation
* FSM-based control unit
* Synchronous design
* Memory-mapped operations

---

## Instruction Cycle

The processor operates using a **4-stage cycle**:

### 1. Fetch

* Instruction is read from Instruction Memory using the PC

### 2. Decode

* Opcode and operands are extracted
* Control Unit generates control signals

### 3. Execute

* ALU operations or memory access are performed

### 4. Finish

* PC is updated
* System prepares for next instruction

---

## Instruction Format

Each instruction is **16 bits**:

```
[15:12] Opcode
[11:10] Rd (Destination Register)
[9:8]   Rs (Source Register)
[7:0]   Address / Immediate
```

### Example

```
1011_00_01_00000101
```

* Opcode: `1011` → ADD
* Rd: `00` → Register 0
* Rs: `01` → Register 1
* Address: `00000101` → Memory address 5

---

## Supported Instructions

| Opcode | Instruction | Description              |
| ------ | ----------- | ------------------------ |
| 0001   | LDA         | Load from memory → Rd    |
| 0010   | INP         | Load input register → Rd |
| 0011   | OUT         | Output register value    |
| 0100   | XOR         | Bitwise XOR              |
| 0101   | BUN         | Branch (PC update)       |
| 0110   | AND         | Bitwise AND              |
| 0111   | OR          | Bitwise OR               |
| 1000   | NOT         | Bitwise NOT              |
| 1001   | SHL         | Shift left               |
| 1010   | SHR         | Shift right              |
| 1011   | ADD         | Addition                 |
| 1100   | SUB         | Subtraction              |

---

## ALU Operations

The ALU supports:

* **Arithmetic:** ADD, SUB
* **Logical:** AND, OR, XOR, NOT
* **Shift:** SHL, SHR

---

## Simulation & Verification

* Designed and tested using **ModelSim / QuestaSim**
* Functional verification performed using testbenches
* Modular testing for individual components before integration

---

## Key Concepts Demonstrated

* RTL Design in VHDL
* Processor Datapath & Control
* Finite State Machine (FSM) Design
* Instruction Decoding
* Memory Interfacing
* Modular Hardware Design

---

## Future Improvements

* Pipeline implementation
* Expanded instruction set
* Hazard detection and forwarding
* Interrupt handling
* Performance optimization

---
## Summary

This project demonstrates the complete design of a **basic processor in VHDL**, combining datapath components, control logic, and memory systems into a functional CPU model.

It serves as a strong foundation for understanding **digital design, computer architecture, and RTL
