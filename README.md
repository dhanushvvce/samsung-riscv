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

## 🚀 **How to Reproduce the Snapshots**
1. Write a simple C program (`sum.c`) in a text editor.
2. Compile using:  
   ```bash
   gcc -g -o sum sum.c
