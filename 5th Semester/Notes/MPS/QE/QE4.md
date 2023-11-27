# Questions
### How do we specify the start of execution after reset?
The vector table specifies the start of execution after reset. The first entry in the vector table is the stack pointer value and the second entry is the address of the reset handler code.

### Which interrupt is the first one to occur on Cortex-M based microcontroller?
The reset interrupt is the first interrupt to occur on a Cortex-M based microcontroller after power on.

### What are the possible sizes (in bits) of an encoded instruction in Thumb2 instruction set architecture?
In Thumb2 instruction set, the encoded instructions can be either 16-bit or 32-bit.

### List the possible fields of an assembly instruction.
The possible fields in an assembly instruction are:
- Mnemonic (ADD, MOV etc)
- Operands (registers, immediates etc)
- Condition code (EQ, NE etc)

### Which assembly instruction fields are mandatory? Also name the optional fields.
The mnemonic and operands are mandatory fields in an assembly instruction. The condition code is an optional field.

### What is the minimum and maximum number of operands that can be used in an assembly instruction?
The minimum number of operands is 0 and maximum is 3.

### Is it possible to transfer data from memory to a register using MOV instruction? If yes, then provide an example.
Yes, data can be transferred from memory to a register using MOV instruction. For example: MOV R1, [R2] ; Load data from memory location in R2 to R1

### Which two operations are combined in CBZ assembly instruction? How is the flexibility compromised in CBZ instruction?
CBZ combines a compare to zero and a branch operation. The flexibility is compromised because the register to compare has to be specified in the instruction and cannot be a variable register operand.

### What are pseudo assembly instruction? Are those executed at compile time or run time?
Pseudo instructions are assembler directives that are not actual processor instructions but provide additional information to the assembler. Pseudo instructions are executed by the assembler at compile time.

### How is the AREA assembler directive used to create code or data sections in the memory?
The AREA assembler directive defines different memory regions for code and data. For example: AREA myData, DATA ; Defines a data section AREA myCode, CODE ; Defines a code section

### Is it possible to create code section in data memory region? If yes, give an example.
Yes it is possible to create a code section in data memory by specifying the CODE attribute. For example: AREA myCode, DATA, CODE ; Creates a code section in data memory

### If an assembly instruction uses one of the high registers (R8-R12) as its operand, then which encoding (16-bit or 32-bit) can be used for this instruction?
If a high register is used, only the 32-bit encoding can be used for the instruction. The 16-bit encoding only supports access to low registers R0-R7.

### List the factors that affect the instruction encoding size.
The factors affecting encoding size are:
- Type of registers used (low vs high)
- Immediate value size
- Accessing PC or SP
- Certain instruction types (CBZ, POP, PUSH etc)

# Exercise
### What are assembler directives? How are they different from assembly instructions?
Assembler directives like AREA, ALIGN, etc. are commands for the assembler and linker to set up memory regions, align data, reserve space etc. Assembly instructions like ADD, MOV are actual processor instructions that get converted to machine code.

### Explain the sequence of steps that are followed after reset.
On reset, the processor loads the stack pointer value from the first entry of the vector table. It then loads the reset handler address from the second entry and jumps to it. The reset handler code will initialize the stacks, data sections, and any peripherals before jumping to the main application.

### How is the stack initialized in assembly language? In assembly language, how will you reserve a stack space of 2048 bytes?
The stack is initialized by loading the stack pointer with the start address of the stack area. For example: LDR SP, =StackStartAddress To reserve 2048 bytes stack: STACK_SIZE EQU 2048 AREA STACK, NOINIT, READWRITE, ALIGN=3 StackMem SPACE STACK_SIZE

### What happens if an assembly instruction starts from the first column? Additionally, is it possible to write two assembly instructions on one line?
If an instruction starts in the first column, it will be treated as a label, causing errors. Two instructions cannot be put on one line, each instruction must be on a separate line.

### Modify the program given in Example 4.1 so that we can find the sum of the first 10 odd numbers.
Here is the modified program:

; R0 will hold the sum MOV R0, #0

; R1 is the counter register MOV R1, #1

loop: ADDS R0, R0, R1 ; Add current odd number to sum ADDS R1, R1, #2 ; Increment counter by 2 for next odd number CMP R1, #20  
BLT loop ; Repeat till R1 < 20

### Write a program in Assembly language so that it determines the sum of the five even numbers starting from 20.
Here is the program:
MOV R0, #0 ; R0 holds sum MOV R1, #20 ; R1 holds current number
loop: ADDS R0, R0, R1 ; Add current number to sum ADDS R1, R1, #2 ; Increment number by 2 CMP R1, #36 BLT loop ; Repeat if R1 < 36

### Execute the program given in Listing 4.8 and confirm that it works correctly. Modify it by assigning the Data AREA of X and Y the READWRITE attribute and see its impact on the working of the program. In case it does not work properly, try to find the reason for it.
Making the X and Y variables writable will lead to the code trying to write to read-only memory and cause a fault. This is because the linker has placed those variables in read-only .text section as they were marked READONLY initially.

### Explain the functionality of the following assembly program. What will be the contents of the 'dst_data' string?
The program loads values from a read-only array src_data, multiplies them by SLOPE and adds OFFSET. The results are stored to the array dst_data.

dst_data will contain: 11, 17, 23, 29

### Figure 4.9 shows the memory contents of an ARM processor. Write the contents of PC, SP, R0, and R1 after every instruction cycle, starting from the processor reset. Show contents for PC, SP, R0, and R1 registers for first five instruction cycles.
Cycle 1: PC: 0x40000000 SP: 0x20001000 R0: UNKNOWN R1: UNKNOWN

Cycle 2: PC: 0x400002A4 SP: 0x20001000  
R0: 0xF0F0 R1: UNKNOWN

Cycle 3:  
PC: 0x400002A8 SP: 0x20001000 R0: 0xF0F0 R1: UNKNOWN

Cycle 4: PC: 0x400002AC SP: 0x20001000 R0: 0xF0F0  
R1: 0xF0F0

Cycle 5: PC: 0x400002AC SP: 0x20001000 R0: 0xF0F0 R1: 0xF0F0

### Whether the following instructions are encoded as 16-bit or 32-bit, if 32-bit encoding is used, give the reason why 16-bit encoding is not possible for that case.
```arm-asm
SUBS R2, R2, #8 ; 16-bit ADDS R8, R6, #4 ; 32-bit (R8 is high register) MOV R2, R5 ; 16-bit MOV R2, #0x8C30 ; 32-bit (16-bit cannot encode large immediate value)
```

### An assembler translates the assembly instructions to the corresponding machine codes. In Figure 4.10 are a few instructions with their encoding formats. Using the above-mentioned encoding formats; decode the following machine codes to the corresponding assembly instructions.

0x3213: ADDS R2, R1, #0x10
0xF24F00FE: MOVW R0, #0xFF00

### If an instruction is encoded using 16-bit encoding, is it possible to encode the same instruction using 32-bit encoding? If 0x3213 is the 16-bit machine code of an instruction, then if possible, what will be the 32-bit machine code for the same instruction?
Yes, 16-bit encoded instructions can also be encoded in 32-bit format. For machine code 0x3213, the 32-bit encoding is: 0xF2031013