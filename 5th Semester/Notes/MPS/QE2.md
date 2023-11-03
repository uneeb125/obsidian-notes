# Questions
### Thumb vs ARM
In Thumb mode, the instructions are 16-bit wide. In ARM mode, the instructions can be 32-bit or 16-bit wide.

### Thumb2 mode
In Thumb2 mode, most instructions are 32-bit wide, with some 16-bit wide instructions also supported.

### Thumb 2 perf
Thumb2 provides better performance in terms of both speed and code density compared to Thumb and ARM. It has 16 and 32-bit instructions to optimize code density and performance.
![[Thumb2 comparision.png]]

### 16-bit higher reg access
No, 16-bit Thumb instructions cannot access high registers R8-R12 directly. Only 32-bit Thumb2 instructions can do that.

### Banked Register
The SP (R13) register has two physical copies SP_process and SP_main, access controlled by a privileged control bit. The SP and PC have only one copy each.

![[Register map (M3).png]]
### Special Purpose Registers
- **Program Status Registers:**
	- Application 
	- Interrupt  
	- Execution 
- **Interrupt Mask Registers:**
	- *PRIMASK*: All except NMI and Hardfault masked
	- *FAULTMASK*: All except NMI masked
	- *BASEPRI*: All at or below a certain set value masked
- **Control Register**

### LR modify in subroutine
If LR is modified inside a subroutine, it will corrupt the return address of the calling function. This will lead to a crash or unexpected behavior.
Push it to stack at subroutine start so that it can be restored before subroutine exit.

### Operation mode
- **Thread mode**: 
	- Privileged or Unprivileged
- **Handler mode**
	- Privileged (only)
### Control bit
- **Bit 0** controls the **privilege level** (privileged or unprivileged) in thread mode.
- **Bit 1** controls which **stack pointer** (MSP or PSP) is used.

| Control Bit | Description      |
|:-----------:| ---------------- |
|   0    0    | Privileged   MSP |
|   0    1    | Privileged   PSP |
|   1    0    | Unprivileged MSP |
|   1    1    | Unprivileged PSP | 

### Unprivileged Thread mode access
No, in thread mode with unprivileged access, the processor cannot directly modify PC or LR. It can only modify PC by performing a branch instruction.

### Reset Sequence
- **Address 0 x 00000000:** This address in the code memory (most likely a Flash memory) contains the starting value that is loaded to the **main stack pointer, MSP (R 13).**
- **Address 0 x 00000004:** **Reset vector** is contained at this address and the program counter is loaded with this value to jump to the reset interrupt service routine.
The main function is called from within reset interrupt service routine.

### Stages in Processor
- **Common 3 stage:** 
	- Fetch
	- Decode
	- Execute.
- **RISC 5-stage:** 
	- Instruction Fetch
	- Decode
	- Execute
	- Memory access
	- Register file rightback

### Memory Map
![[Memory map.png]]
- SRAM used for data

### Effect of Endianess
No, endianness does not matter if all accesses are byte sized. It only matters for larger data types like halfword, word etc.

### Which bus is used to access Data
The DCode bus is used to access the data memory region.

### Uses of the stack
The stack is used to store temporary data, function parameters, return addresses, local variables etc.

### Pre-requisites to using a stack
To use the process stack (PSP) in thread mode
- CONTROL register needs to be configured to use PSP (bit-1 set to 1)
- The process stack pointer (PSP) register needs to be initialized to point to a valid region of memory to be used as the stack.

### 
Advantages of bit banding: Allows atomic read-modify-write on single bits. Disadvantage: Wastes memory as each bit requires a 32-bit word.

Debug interfaces on Cortex-M: JTAG, SWD, ETB, DAP. SWD is used for debugging, breakpoint management, and memory access.