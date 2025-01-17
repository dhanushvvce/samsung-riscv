# Understanding RISC-V and Its Instruction Formats

## Overview
RISC-V is an open-source Instruction Set Architecture (ISA) based on Reduced Instruction Set Computing (RISC) principles. It offers a free, modular, and extensible platform for designing processors tailored to specific applications. Unlike proprietary ISAs, RISC-V is open and license-free, making it a popular choice in academia, research, and industry.

This repository provides an in-depth explanation of RISC-V’s six primary instruction formats and demonstrates how they are structured.

---

## What is an Instruction Format?
An instruction format defines the structure of a machine-level instruction, determining how data and operations are encoded for execution. RISC-V instructions are always **32 bits** long, and they follow specific formats for different types of operations.

---

## RISC-V Instruction Formats
RISC-V defines six main instruction formats, each designed for specific use cases:

1. **R-type (Register-Type):** Used for arithmetic and logical operations.
2. **I-type (Immediate-Type):** Used for operations involving immediate values.
3. **S-type (Store-Type):** Used for storing data into memory.
4. **B-type (Branch-Type):** Used for conditional branching.
5. **U-type (Upper-Immediate):** Used for loading upper immediate values.
6. **J-type (Jump-Type):** Used for jump operations.

<img width="772" alt="instructions_types" src="https://github.com/user-attachments/assets/ed5e6db3-985b-42ea-9ea5-4a87bb91bcf6" />


---

### 1. R-type Instruction
R-type instructions operate on registers and are used for computations like addition, subtraction, and logical operations.

**Structure:**
| Field   | Size  | Description                        |
|---------|-------|------------------------------------|
| Opcode  | 7 bits| Instruction type                  |
| rd      | 5 bits| Destination register              |
| func3   | 3 bits| Specifies operation type          |
| rs1     | 5 bits| First source register             |
| rs2     | 5 bits| Second source register            |
| func7   | 7 bits| Additional operation specification|

**Example:**
- Instruction: `ADD r9, r2, r5`  
- Operation: Add the values in `r2` and `r5` and store the result in `r9`.

**Encoding Breakdown:**
- Opcode: `0110011`
- rd: `r9` → `01001`
- rs1: `r2` → `00010`
- rs2: `r5` → `00101`
- func3: `000`
- func7: `0000000`

**Final Instruction:**  
`0000000_00101_00010_000_01001_0110011`

![image](https://github.com/user-attachments/assets/4da66991-8ae7-4568-8654-d4620591a7e7)


---

### 2. I-type Instruction
I-type instructions work with a register and an immediate value. These are commonly used for operations like loading values or arithmetic with constants.

**Structure:**
| Field   | Size  | Description                        |
|---------|-------|------------------------------------|
| Opcode  | 7 bits| Instruction type                  |
| rd      | 5 bits| Destination register              |
| func3   | 3 bits| Specifies operation type          |
| rs1     | 5 bits| Source register                   |
| imm     | 12 bits| Immediate value                  |

**Example:**
- Instruction: `ADDI r12, r4, 5`  
- Operation: Add `5` to the value in `r4` and store the result in `r12`.

**Encoding Breakdown:**
- Opcode: `0010011`
- rd: `r12` → `01100`
- rs1: `r4` → `00100`
- imm: `000000000101`
- func3: `000`

**Final Instruction:**  
`000000000101_00100_000_01100_0010011`

![image](https://github.com/user-attachments/assets/bd38c8be-4303-4372-a796-c6d33cb2bd6e)

---

### 3. S-type Instruction
S-type instructions store data from registers into memory.

**Structure:**
| Field   | Size  | Description                        |
|---------|-------|------------------------------------|
| Opcode  | 7 bits| Instruction type                  |
| rs1     | 5 bits| Base address register             |
| rs2     | 5 bits| Source register                   |
| imm[11:5]| 7 bits| Upper immediate bits             |
| imm[4:0] | 5 bits| Lower immediate bits             |
| func3   | 3 bits| Operation type                    |

**Example:**
- Instruction: `SW r3, 2(r1)`  
- Operation: Store the value in `r3` at the memory location `r1 + 2`.

**Final Instruction:**  
`0000000_00011_00001_010_00010_0100011`

![i type (1)](https://github.com/user-attachments/assets/297f75f7-b755-4064-bdbe-281964e6107c)






---

### 4. B-type Instruction
B-type instructions perform conditional branching.

**Structure:**
| Field   | Size  | Description                        |
|---------|-------|------------------------------------|
| Opcode  | 7 bits| Instruction type                  |
| rs1     | 5 bits| Source register 1                 |
| rs2     | 5 bits| Source register 2                 |
| imm     | 13 bits| Branch offset                    |
| func3   | 3 bits| Branch condition                  |

**Example:**
- Instruction: `BNE r0, r1, 20`  
- Operation: Branch to `PC + 20` if `r0 ≠ r1`.

![image](https://github.com/user-attachments/assets/5cc9b638-da88-47f3-b0aa-396f4f748c63)





---

### 5. U-type Instruction
U-type instructions are used to load immediate values into the upper bits of a register.

**Structure:**
| Field   | Size  | Description                        |
|---------|-------|------------------------------------|
| Opcode  | 7 bits| Instruction type                  |
| rd      | 5 bits| Destination register              |
| imm     | 20 bits| Upper immediate value            |

![image](https://github.com/user-attachments/assets/e823512f-82e7-4dac-a02d-7d2634dfec24)


---

### 6. J-type Instruction
J-type instructions perform jump operations, often used for loops or function calls.

**Structure:**
| Field   | Size  | Description                        |
|---------|-------|------------------------------------|
| Opcode  | 7 bits| Instruction type                  |
| rd      | 5 bits| Destination register              |
| imm     | 20 bits| Jump offset                      |


![image](https://github.com/user-attachments/assets/6c501798-bd28-4312-ba66-7adc2a2a851a)



# RISC-V 15 Unique Instructions and Their 32-Bit Machine Codes
I've identified 15 unique RISC-V instructions from the object file, and for each instruction to determine its exact 32-bit machine code in the format `opcode rd, rs, immediate`to ensure the instruction type and operations are clearly specified.


![image](https://github.com/user-attachments/assets/972543b0-1292-4edc-8f37-37914593f509)


### **R-Type Instructions**  
Format: `opcode | rd | funct3 | rs1 | rs2 | funct7`

1. **`add s0, s0, 8`**  
   **Instruction Code**: `00828293`  
   **Expanded**: `0000000 | 1000 | 010 | 00010 | 01010 | 0110011`  

---

### **I-Type Instructions**  
Format: `immediate | rs1 | funct3 | rd | opcode`

2. **`li a0, 45`** (Load Immediate)  
   **Instruction Code**: `00800593`  
   **Expanded**: `0000000000101101 | 00000 | 000 | 01010 | 0010011`  

3. **`ld ra, 8(sp)`** (Load Doubleword)  
   **Instruction Code**: `00812083`  
   **Expanded**: `0000000000001000 | 00010 | 011 | 00010 | 0000011`  

4. **`jalr a5, ra, 0`** (Jump and Link Register)  
   **Instruction Code**: `000f8067`  
   **Expanded**: `0000000000000000 | 11110 | 000 | 11111 | 1100111`  

---

### **S-Type Instructions**  
Format: `immediate[11:5] | rs2 | rs1 | funct3 | immediate[4:0] | opcode`

5. **`sw ra, 8(sp)`** (Store Word)  
   **Instruction Code**: `00f12223`  
   **Expanded**: `0000000 | 11110 | 00010 | 010 | 01000 | 0100011`  

6. **`sd ra, 16(sp)`** (Store Doubleword)  
   **Instruction Code**: `00a12023`  
   **Expanded**: `0000000 | 11110 | 00010 | 011 | 10000 | 0100011`  

---

### **B-Type Instructions**  
Format: `immediate[12|10:5] | rs2 | rs1 | funct3 | immediate[4:1|11] | opcode`

7. **`beqz a5, <exit+0x2c>`** (Branch if Equal to Zero)  
   **Instruction Code**: `fe010ee3`  
   **Expanded**: `1111111 | 11111 | 00010 | 000 | 11100 | 1100011`  

---

### **U-Type Instructions**  
Format: `immediate[31:12] | rd | opcode`

8. **`lui a0, 0x23150`** (Load Upper Immediate)  
   **Instruction Code**: `23150537`  
   **Expanded**: `0010001101010000 | 01010 | 0110111`  

9. **`auipc a5, 0x477`** (Add Upper Immediate to PC)  
   **Instruction Code**: `47728097`  
   **Expanded**: `0100011101110111 | 01000 | 0010111`  

---

### **J-Type Instructions**  
Format: `immediate[20|10:1|11|19:12] | rd | opcode`

10. **`jal ra, <printf>`** (Jump and Link)  
    **Instruction Code**: `000080e7`  
    **Expanded**: `0000000000001000 | 00000 | 1101111`  

11. **`j <exit>`** (Jump)  
    **Instruction Code**: `4300006f`  
    **Expanded**: `0100001100000000 | 00000 | 1101111`  

---






