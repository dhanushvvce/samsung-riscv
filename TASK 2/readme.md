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








