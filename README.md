# samsung-riscv
## Basic Details

Name: DHANUSH N

College: Vidyavardhaka College of Engineering

Email ID: dhanushn200304@gmail.com

GitHub Profile: dhanushvvce

LinkedIN Profile: https://www.linkedin.com/in/dhanush-n-779145211/

<details>
<summary> <b>Task 1</b></summary>
<br>
The task involves referring to lab videos on C programming and RISC-V, and performing the compilation of C code using both the GCC compiler and the RISC-V compiler.
   
## C Language
### Compilation using GCC Compiler

Steps to compile any `.c` file :

1. Open the bash terminal and navigate to the directory where you want to create your file.
2. Run the following command to create and open the file in the editor:
   ```bash
   gedit sum1ton.c
3. Use these commands to run the C code:
    ```bash
   gcc sum1ton.c
   ./a.out
![sum1ton code](https://github.com/user-attachments/assets/1d88196a-812d-4977-bc33-75df96489417)

## RISC-V
Compile the code using the RISC-V GCC compiler using these commands:
1. Display c code:
   ```bash
   cat sum1ton.c
2. Command to compile code
   ```
   riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
3. Displays the assembly language code
   ```
   riscv64-unknown-elf-objdump -d sum1ton.o
![riscv1](https://github.com/user-attachments/assets/0aa98971-6197-417c-9e0a-6d9d5a561225)

4. Type `/main` to locate the main section in code
   
![RISCV2](https://github.com/user-attachments/assets/a844c11d-190c-4347-b937-49bc490f7166)

</details>

<details>
<summary><b>Task 2</b></summary>
<br>
This task involves comparing two optimization levels, -O1 and -Ofast, while debugging a simple C program using SPIKE.

## Debugging with SPIKE

![VirtualBox_vdsworkshop_13_01_2025_19_06_42](https://github.com/user-attachments/assets/cbd9a387-1df4-40c2-aa91-e320ec984e4e)

The C code was compiled

In order to balance compilation time and performance, the -O1 optimisation option offers modest optimisation. It's perfect for a combination of performance enhancements that don't significantly affect debugging. Conversely, -Ofast aggressively optimises for optimal performance, even at the expense of adhering to some standard-compliant behaviours and possibly making debugging more difficult.
The code undergoing these optimisations can be seen in the attached file.

![VirtualBox_vdsworkshop_13_01_2025_20_52_37](https://github.com/user-attachments/assets/dd1b5a49-59ba-4201-b9de-1f3920afdd64)

Each optimisation level's RISC-V object dump (-O1 and -Ofast).

By disassembling the object file, the riscv64-unknown-elf-objdump tool reveals the machine code produced by each optimisation level:
The code undergoing these optimisations can be seen in the attached file.

![VirtualBox_vdsworkshop_13_01_2025_20_45_01](https://github.com/user-attachments/assets/0a9328fe-86de-4102-adf0-a6120fb4bfdf)

![VirtualBox_vdsworkshop_13_01_2025_20_44_40](https://github.com/user-attachments/assets/f4baee36-9df7-4291-91d4-aa6b0540f90a)

</details>

<details>
<summary><b>Task 3</b></summary>
<br>
   
# RISC-V and Its Instruction Formats

## Overview of RISC-V
RISC-V is an open-source Instruction Set Architecture (ISA) that allows developers to design processors optimized for specific applications. Built on the principles of Reduced Instruction Set Computer (RISC), RISC-V represents the fifth generation of processors following this concept. Its open and free design enables developers to utilize RISC-V without licensing fees, making it an appealing alternative to proprietary processor architectures.

---

## Instruction Formats in RISC-V
An instruction format outlines the structure of machine language instructions executed by a processor. These instructions, composed of binary data (0s and 1s), provide details on data locations and operations.

RISC-V defines six primary instruction formats:

1. **R-format**
2. **I-format**
3. **S-format**
4. **B-format**
5. **U-format**
6. **J-format**

Below is a detailed explanation of each format.

---

### 1. R-type Instructions
**R-type (Register-type)** instructions work with registers rather than memory locations and are used for arithmetic and logical operations.

#### Structure:
| Field Name | Size   | Description                     |
|------------|--------|---------------------------------|
| Opcode     | 7 bits | Specifies the instruction type  |
| rd         | 5 bits | Destination register            |
| func3      | 3 bits | Defines the operation type      |
| rs1        | 5 bits | First source register           |
| rs2        | 5 bits | Second source register          |
| func7      | 7 bits | Additional operation specifier  |

#### Example: ADD r9, r2, r5
- **Operation**: Adds the values in registers `r2` and `r5`, storing the result in `r9`.
- **32-bit Instruction**: `0000000_00101_00010_000_01001_0110011`

---

### 2. I-type Instructions
**I-type (Immediate-type)** instructions utilize a register and an immediate (constant) value. These are commonly used for load and immediate operations.

#### Structure:
| Field Name | Size   | Description                     |
|------------|--------|---------------------------------|
| Opcode     | 7 bits | Specifies the instruction type  |
| rd         | 5 bits | Destination register            |
| func3      | 3 bits | Defines the operation type      |
| rs1        | 5 bits | Source register                 |
| imm[11:0]  | 12 bits| Immediate value                 |

#### Example: ADDI r12, r4, 5
- **Operation**: Adds the immediate value `5` to the value in `r4` and stores it in `r12`.
- **32-bit Instruction**: `000000000101_00100_000_01100_0010011`

---

### 3. S-type Instructions
**S-type (Store-type)** instructions write register values to memory locations.

#### Structure:
| Field Name | Size   | Description                     |
|------------|--------|---------------------------------|
| Opcode     | 7 bits | Specifies the instruction type  |
| rs1        | 5 bits | Base address register           |
| rs2        | 5 bits | Source register                 |
| imm[11:5]  | 7 bits | Upper immediate value           |
| imm[4:0]   | 5 bits | Lower immediate value           |
| func3      | 3 bits | Defines the operation type      |

#### Example: SW r3, 2(r1)
- **Operation**: Stores the value in `r3` to the memory address `r1 + 2`.
- **32-bit Instruction**: `0000000_00011_00001_010_00010_0100011`

---

### 4. B-type Instructions
**B-type (Branch-type)** instructions manage branching based on conditions.

#### Structure:
| Field Name | Size   | Description                     |
|------------|--------|---------------------------------|
| Opcode     | 7 bits | Specifies the instruction type  |
| rs1        | 5 bits | First source register           |
| rs2        | 5 bits | Second source register          |
| imm        | 12 bits| Immediate value for branching   |
| func3      | 3 bits | Defines the branch condition    |

#### Example: BNE r0, r1, 20
- **Operation**: Branches to the address `PC + 20` if `r0` is not equal to `r1`.
- **32-bit Instruction**: `0000000_00001_00000_001_10100_1100011`

---

### 5. U-type Instructions
**U-type (Upper Immediate)** instructions load immediate data into the destination register.

#### Structure:
| Field Name | Size   | Description                     |
|------------|--------|---------------------------------|
| Opcode     | 7 bits | Specifies the instruction type  |
| rd         | 5 bits | Destination register            |
| imm[31:12] | 20 bits| Upper immediate value           |

---

### 6. J-type Instructions
**J-type (Jump-type)** instructions enable jump operations, often used for implementing loops.

#### Structure:
| Field Name | Size   | Description                     |
|------------|--------|---------------------------------|
| Opcode     | 7 bits | Specifies the instruction type  |
| rd         | 5 bits | Destination register            |
| imm        | 20 bits| Immediate value for jump        |

---

### An overview image of the instructions is provided below

![RISCV_32-bit-instruction](https://github.com/user-attachments/assets/13fa70a9-4f3c-4d92-8ad3-5b53cca14eb7)

---

## RISC-V 15 unique instructions and their 32-bit machine codes

![VirtualBox_vdsworkshop_17_01_2025_19_47_26](https://github.com/user-attachments/assets/78c6d21a-8dc7-4712-a4a8-39a1a63739e0)

15 unique RISC-V instruction is picked from the above image and their machine code, opcode, format and instruction binary are specified below.

| Instruction             | Opcode   | Format  | Machine Code | Binary Representation                                             |
|-------------------------|----------|---------|--------------|---------------------------------------------------------------------|
| `addi sp, sp, -16`      | 0010011  | I-type  | `ff010113`   | `11111111000000010000000100010011`                                 |
| `sd ra, 8(sp)`          | 0100011  | S-type  | `00813023`   | `00000000100000011001000000100011`                                 |
| `li a3, 30`             | 0010011  | I-type  | `01e00693`   | `00000001111000000000011010010011`                                 |
| `jal ra, 10408`         | 1101111  | J-type  | `268000ef`   | `00100110100000000000000011101111`                                 |
| `ld ra, 8(sp)`          | 0000011  | I-type  | `00813083`   | `00000000100000011001000010000011`                                 |
| `ret`                   | 1100111  | I-type  | `00008067`   | `00000000000000001000000001100111`                                 |
| `mv a1, a0`             | 0010011  | I-type  | `00050593`   | `00000000000001010000010110010011`                                 |
| `j 12df8`               | 1101111  | J-type  | `4390206f`   | `01000011001100000010000001101111`                                 |
| `mv s0, a0`             | 0010011  | I-type  | `00050413`   | `00000000000001010000010000010011`                                 |
| `jalr a5`               | 1100111  | I-type  | `000780e7`   | `00000000000001111000000011100111`                                 |
| `beqz a5, 101f0`        | 1100011  | B-type  | `00078463`   | `00000000000001111000010001100011`                                 |
| `mv a0, s0`             | 0010011  | I-type  | `00040513`   | `00000000000001000000010100010011`                                 |
| `jal ra, 1f134`         | 1101111  | J-type  | `7410e0ef`   | `01110100000100001110000011101111`                                 |
| `auipc a5, 0x12`        | 0010111  | U-type  | `00012797`   | `00000000000100100001011110010111`                                 |
| `beq a5, a0, 101f0`     | 1100011  | B-type  | `00a78563`   | `00000000101001111000010101100011`                                 |

This table summarizes RISC-V instructions, detailing their opcodes, formats, machine codes, and binary representations. These instructions include basic arithmetic, control flow, and memory operations for reference.


</details>

<details>
<summary> <b>Task 4</b></summary>
<br>

Installed iverilog and GTKwave 

![VirtualBox_vdsworkshop_23_01_2025_16_56_05](https://github.com/user-attachments/assets/9727fdde-e6b7-42ff-b868-6c2182a4ce8f)

---

A directory named chethan was created 
```bash
mkdir chethan
```
The following commands were executed

![VirtualBox_vdsworkshop_23_01_2025_16_17_14](https://github.com/user-attachments/assets/bcec5209-824e-4cb2-94b1-ffa63434993c)

---

The below waveform was generated

![VirtualBox_vdsworkshop_23_01_2025_16_26_23](https://github.com/user-attachments/assets/52081c24-a338-4b58-a910-434054968ef2)


</details>
