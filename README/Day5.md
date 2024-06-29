## Day 5:  C code compilation using gcc and RISC-V compilers. 

First, we will use leafpad code editor for writing the code and gcc compiler for the compilation. 

1. Install leafpad editor if not already installed

       sudo apt install leafpad

2. Open leafpad editor

       leafpad filename.c

3. Use gcc compiler to compile the c code

       gcc filename.c
   
5. Execute the code

        ./a.out

Example run: 


![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/bb5905c0-2361-47cc-86cf-3d26955340f5)


Again, we will run the same code using RISC-V compiler 

1. Open the terminal and display our original code file in terminal

       cat sum1ton.c

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/f389ad03-a1a1-436a-80a2-e8bce4fd079a)

2. Compile the c code using RISC-V compiler

       riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c

3. On the new terminal tab, run the following code to display the assembly language equivalent of our c file.

       riscv64-unknown-elf-objdump -d sum1ton.o
       riscv64-unknown-elf-objdump -d sum1ton.o | less
       /main
![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/40f27b33-a3d4-4924-9166-450659a3f26f)


We try the same commands again with a different optimization technique ( Ofast optimization). 

        riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o fast_sum1ton.o sum1ton.c
        riscv64-unknown-elf-objdump -d fast_sum1ton.o
        riscv64-unknown-elf-objdump -d fast_sum1ton.o | less
        /main
        

![image](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/f6987056-ed2d-465f-8790-bd9b4c747fa9)



From the above example we can observe that with -Ofast optimization, the instruction sets are significantly reduced. 


