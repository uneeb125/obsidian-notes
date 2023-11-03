# Questions
### Thumb vs ARM
In Thumb mode, the instructions are 16-bit wide. In ARM mode, the instructions can be 32-bit or 16-bit wide.

### Thumb2 mode
In Thumb2 mode, most instructions are 32-bit wide, with some 16-bit wide instructions also supported.

### Thumb 2 perf
Thumb2 provides better performance in terms of both speed and code density compared to Thumb and ARM. It has 16 and 32-bit instructions to optimize code density and performance.

### 16-bit higher reg access
No, 16-bit Thumb instructions cannot access high registers R8-R12 directly. Only 32-bit Thumb2 instructions can do that.

### Banked Register
The SP (R13) register has two physical copies SP_process and SP_main, access controlled by a privileged control bit. The SP and PC have only one copy each.

![[Register map (M3).png]]

### LR mod in subroutine
If LR is modified inside a subroutine, it will corrupt the return address of the calling function. This will lead to a crash or unexpected behavior.
Push it to stack at subroutine start so that it can be restored before subroutine exit.


No, in thread mode with unprivileged access, the processor cannot directly modify PC or LR. It can only modify PC by performing a branch instruction.

The first two operations after reset are: 1) Fetch the value of the vector table offset register. 2) Load the PC with the address pointed by the reset vector (offset 0x00).

The three phases are - Fetch, Decode, and Execute.

The default code region is 0x00000000-0x1FFFFFFFF. The default data region is 0x20000000-0x3FFFFFFF.

No, endianness does not matter if all accesses are byte sized. It only matters for larger data types like halfword, word etc.

The DCode bus is used to access the data memory region.

The stack is used to store temporary data, function parameters, return addresses, local variables etc.

To use the process stack (PSP) in thread mode, the CONTROL register needs to be configured to use PSP, and the process stack pointer (PSP) register needs to be initialized to point to a valid region of memory to be used as the stack.

Advantages of bit banding: Allows atomic read-modify-write on single bits. Disadvantage: Wastes memory as each bit requires a 32-bit word.

Debug interfaces on Cortex-M: JTAG, SWD, ETB, DAP. SWD is used for debugging, breakpoint management, and memory access.