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

### Bus Matrix
An AHB interconnection network, allowing data and instruction code transfer simultaneously unless both buses are trying to access the same memory region

### Buses
#### ICode
- AHB-Lite
- Instruction fetch 0 x 000 00000 - 0 x 1FFFFFFF
- Fetches only in word size, (2 Thumb fetch)
#### DCode
- AHB-Lite
- Data access 0 x 000 00000 - 0 x 1FFFFFFF
- No unaligned access
	Bus interface at processor converts to aligned
#### System
- AHB-Lite
- Instruction and data access 0 x 20000000 to 0 x DFFFFFFF and 0 x E 01000000 to 0 x FFFFFFFF
- All transfers are aligned
#### AHB-AP
- 3 implementations
	- SWJ-DP (Serial wire and JTAG)
	- SW-DP
	- no DP
- DP and AP together know as DAP
#### PPB
- 0 x E 0040000 to 0 x E00FFFFF
- Some already used so actual is 0 x E 0042000  to 0 x E00FF000
- Transfer is word aligned

![[Bus System.png]]
![[Memory and Peripherials.png]]
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

## Bit Banding
#### Actual Location
0 x 20000000 − 0 x 200FFFFF (SRAM bit-band region, 1 MB)
• 0 x 40000000 − 0 x 400FFFFF (peripheral bit-band region, 1 MB)
#### Alias Location
• 0 x 22000000 − 0 x 23FFFFFF (SRAM bit-band alias region, 32 MB)
• 0 x 42000000 − 0 x 43FFFFFF (peripheral bit-band alias region, 32 MB)
#### Formula
$$
y = ((0\text{x}F0000000\space \text{\&}\space x)\space |\space 0\text{x}02000000) + ((0\text{x}000FFFFF\space \text{F}\space x))
$$
y = ((0xF0000000 & x) | 0x02000000 + ((0x000FFFFF &x) << 5) + (c << 2)
### Advantages and Disadvantages of Bit banding
**Advantages:** Allows atomic read-modify-write on single bits. 
**Disadvantage:** Wastes memory as each bit requires a 32-bit word.

### M-3 debug interfaces
Debug interfaces on Cortex-M: JTAG, SWD, ETB, DAP. SWD is used for debugging, breakpoint management, and memory access.

### State of bits at reset
On reset, T=1, F=1, I=1.

### ARM with Thumb2
All ARMv7 processors

### Bit band reverse
Bit band alias address = 0x02000000 + (byte_offset_32) + (bit_number_4)

### Using MSP & PSP (not simultaneously)
Yes it is possible if PSP is used for one stack and MSP for another.

### Thumb2 no switch delay
Using more 32-bit Thumb2 instructions instead of 16-bit Thumb instructions.

### Max addressable memory 
Address bus
Max memory size = 2^20 = 1 MB


### Pipelined
Non-pipelined: 200 cycles. Pipelined: 100 * (2/4) = 50 cycles.

### User (unprivileged) to handler
Exceptions

### Poison for pipeline 
Code with lots of branches which cause frequent pipeline flushes.

### Little endian from lower address to higher address
Little endian value: 0x78563412


Bit band alias address = 0x22000008