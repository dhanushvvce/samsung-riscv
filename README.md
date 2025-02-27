# Samsung-RISCV
This course teaches users about VLSI chip design and RISC-V using open-source tools and is based on the RISC-V architecture. Kunal Ghosh Sir is the workshop's instructor.
## Profile Details:
##### Name: Dhanush N
##### College: Vidyavardhaka College of Engineering
##### Email: dhanushn200304@gmail.com
##### GitHub Profile: dhanushvvce
##### LinkedIN: https://www.linkedin.com/in/dhanush-n-779145211
<details>
<summary><b>Task 1:</b>Lab Snapshots: Assembly and C Programming Debugging</summary>   
<br>
# samsung-riscv

# 📊 **Lab Snapshots: Assembly and C Programming Debugging**

## 📑 **Overview**
This repository contains snapshots from a technical lab session focusing on **Assembly-level debugging**, **C programming**, and **Memory Analysis**. These images showcase code execution, disassembly views, and error analysis during program execution.

---

## 🛠️ **Snapshots Description**

### 🖥️ **1. Assembly-Level Debugging Snapshot**
- **Description:** Analysis of low-level assembly instructions from a compiled program.
- **Key Focus:**
   - Register-level operations.
   - Memory address references.
   - Function call traces.
- **Purpose:** Understand how high-level C code maps to machine instructions.

---

### 📝 **2. C Program Snapshot**
- **Description:** Simple C program to calculate the **sum of numbers from 1 to n** using a loop.
- **Key Focus:**
   - Syntax and logic analysis.
   - Debugging `printf` statements.
   - Correct usage of loops.
- **Purpose:** Identify and resolve logical and syntactical errors in the C code.

---

### ⚙️ **3. Assembly Disassembly Snapshot**
- **Description:** Detailed disassembly of the **main function** in an executable.
- **Key Focus:**
   - Conditional branching.
   - Stack and heap memory operations.
   - Instruction-level execution.
- **Purpose:** Optimize and debug program execution at the machine level.

---

## 📚 **Technologies Used**
- **Programming Language:** C
- **Tools:** GCC Compiler, GDB Debugger, Terminal
- **OS Environment:** Linux/Ubuntu (Virtual Machine)

---

![riscvdi2](https://github.com/user-attachments/assets/4c0c01b1-0fb0-4182-b5da-029b5038eb10)
![riscvdi3](https://github.com/user-attachments/assets/11c55d68-3607-4f9c-be56-312e39f43dbd)
![riscvdi1](https://github.com/user-attachments/assets/5d775210-4d43-4cf2-838c-dc44b43849ff)
</details>
<details>
  
<summary><b>Task 2:</b>Task 2:Task is to refer to C based and RISCV based lab videos and execute the task of compiling the C code using gcc and riscv compiler simulator </summary>   
<br>
##    TASK 2,RISC V

This task involves comparing two optimization levels, -O1 and -Ofast, while debugging a simple C program using SPIKE.

The compiled C code

The -O1 optimization option provides moderate optimization to balance performance and compilation time. It's ideal for a blend of performance improvements without heavily impacting the debugging process. On the other hand, -Ofast optimizes aggressively for maximum performance, even at the cost of adherence to some standard-compliant behaviors and potentially more challenging debugging.

The provided file contains the code subject to these optimizations.

![RISCV TASK2 IMAGE 1](https://github.com/user-attachments/assets/7dd922d9-4d62-44b2-8ae8-2271f6c9b795)

The RISC-V object dump for each optimization level (-O1 and -Ofast).

The riscv64-unknown-elf-objdump command disassembles the object file, providing insight into the machine code generated by each optimization level:

The provided file contains the code subject to these optimizations.

![RISC V TASK2 IMAGE 2](https://github.com/user-attachments/assets/4926c807-809d-46ec-9378-5e20d8dc8337)

![RISC V TASK 2 IMAGE 3](https://github.com/user-attachments/assets/90659035-24fd-43d4-bc4e-b86057b1014b)
</details>
<details>   
<summary><b>Task 3:</b> Understanding RISC-V and Its Instruction Formats</summary>   
<br>
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
</details>
<details>   
<summary><b>Task 4:</b>Installed iverilog and GTKwave</summary>   
<br>
# Samsung-riscv

# Task-4


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
<details>   
<summary><b>Task 5:</b> Intruder Detection System Using IR Sensor & VSDSquadron Mini</summary>   
<br>

# **IR Sensor-Based Hurdle Detection with LED Alert (RISC-V Board)**  

## **Project Overview**  
This project demonstrates **hurdle detection** using an **Infrared (IR) sensor** interfaced with a **RISC-V development board**. The system continuously monitors for obstacles, and when one is detected, an **LED indicator lights up** or blinks as an alert. This setup is useful for applications such as **autonomous robots, security systems, and smart automation**.  

---

## **Hardware Components**  
To build this project, you will need:  
- **RISC-V Development Board** 
- **IR Proximity Sensor**  
- **LED** (for visual indication)  
- **Resistor (330Ω)** (for LED current limiting)  
- **Connecting jumper Wires**  
- **Breadboard** 

---

## **How It Works**  
1. The **IR sensor** emits infrared light and detects reflections from nearby objects.  
2. If an object is detected, the **IR sensor outputs a LOW signal**; otherwise, it remains HIGH.  
3. The **RISC-V board reads the sensor signal** and processes the data.  
4. If an obstacle is detected, the **LED turns ON or blinks**, providing a visual alert.  
5. The system continuously checks for obstacles in a loop.  

---

## **Circuit Connections**  
| Component         | Pin Connection (RISC-V Board) |
|------------------|-----------------------------|
| **IR Sensor VCC**  | **3.3V / 5V**                               |
| **IR Sensor OUT**  | **GPIO (GPIO5)**      |
| **LED Anode (+)**  | **GPIO (GPIO6)**     |
| **LED Cathode (-)**| **GND**                     |


```c
#include <ch32v00x.h>
#include <debug.h>

void GPIO_Config(void) {
    GPIO_InitTypeDef GPIO_InitStructure = {0};
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);
    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_4;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_6;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
}

int main(void) {
    uint8_t IR = 0;
    uint8_t set = 1;
    uint8_t reset = 0;
    
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);
    SystemCoreClockUpdate();
    Delay_Init();
    GPIO_Config();
    
    while(1) {
        IR = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_4);
        if (IR == 1) {
            GPIO_WriteBit(GPIOD, GPIO_Pin_6, reset);
        } else {
            GPIO_WriteBit(GPIOD, GPIO_Pin_6, set);
        }
        Delay_Ms(100);
    }
}
```



---


</details>
<details>   
<summary><b>Task 6:</b> Intruder Detection using IR Sensor</summary>   
<br>

# **IR Sensor-Based Hurdle Detection with LED Alert (RISC-V Board)**  

## **Project Overview**  
This project demonstrates **hurdle detection** using an **Infrared (IR) sensor** interfaced with a **RISC-V development board**. The system continuously monitors for obstacles, and when one is detected, an **LED indicator lights up** or blinks as an alert. This setup is useful for applications such as **autonomous robots, security systems, and smart automation**.  

---

## **Hardware Components**  
To build this project, you will need:  
- **RISC-V Development Board** 
- **IR Proximity Sensor**  
- **LED** (for visual indication)  
- **Resistor (330Ω)** (for LED current limiting)  
- **Connecting jumper Wires**  
- **Breadboard** 

---

## **How It Works**  
1. The **IR sensor** emits infrared light and detects reflections from nearby objects.  
2. If an object is detected, the **IR sensor outputs a LOW signal**; otherwise, it remains HIGH.  
3. The **RISC-V board reads the sensor signal** and processes the data.  
4. If an obstacle is detected, the **LED turns ON or blinks**, providing a visual alert.  
5. The system continuously checks for obstacles in a loop.  

---

## **Circuit Connections**  
| Component         | Pin Connection (RISC-V Board) |
|------------------|-----------------------------|
| **IR Sensor VCC**  | **3.3V / 5V**                               |
| **IR Sensor OUT**  | **GPIO (GPIO5)**      |
| **LED Anode (+)**  | **GPIO (GPIO6)**     |
| **LED Cathode (-)**| **GND**                     |


```c
#include <ch32v00x.h>
#include <debug.h>

void GPIO_Config(void) {
    GPIO_InitTypeDef GPIO_InitStructure = {0};
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);
    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_4;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_6;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOD, &GPIO_InitStructure);
}

int main(void) {
    uint8_t IR = 0;
    uint8_t set = 1;
    uint8_t reset = 0;
    
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_1);
    SystemCoreClockUpdate();
    Delay_Init();
    GPIO_Config();
    
    while(1) {
        IR = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_4);
        if (IR == 1) {
            GPIO_WriteBit(GPIOD, GPIO_Pin_6, reset);
        } else {
            GPIO_WriteBit(GPIOD, GPIO_Pin_6, set);
        }
        Delay_Ms(100);
    }
}
```



---
