# Questions
### Word, half word, byte access
Addresses that are multiples of 4 bytes will result in word aligned accesses. Addresses that are multiples of 2 bytes (and not multiple of 4 bytes) will result in halfword aligned accesses. Other addresses will result in byte aligned accesses.

### Methods for inter-microcontroller communication
- Parallel communication using GPIO/data bus pins
- Serial communication like I2C, SPI, UART
- Network communication like CAN, Ethernet

### Debugging methods
- Toggle GPIO pins to observe code flow
- Use debugger software and hardware interfaces like JTAG/SWD
- Use debug LEDs and messages
- Use oscilloscope to analyze signals
- Use logic analyzer to capture digital signals
- Insert debug messages and print statements

### Harvard Faster execute
In Harvard architecture, instruction fetch can occur in parallel with data access as they use separate memories and buses. This results in faster overall execution.

### Risc Complex Compilers
RISC has fixed format simple instructions. Complex functions need more instructions. This makes compiler design more complex to optimize performance.

### What does 32-bit processor mean
The 32-bit designation refers to the width of the data bus.

### Differentiating set architectures
Instruction set architecture attributes:
- CISC vs RISC
- Fixed vs Variable length instructions
- Addressing modes
- Number of general purpose registers
- Hardware vs Software interrupts

### Assembler and Object code execution
Assembler converts assembly code to machine code. The object code from assembler cannot be directly executed and needs to be linked.

### Linker
Linker combines multiple object files and libraries and resolves references between them to create an executable. 

### Debugging tools
![[Debugging tools.png]]


### Microcontroller vs Microprocessor
| Microcontroller                 | Microprocessor                          |
| ------------------------------- | --------------------------------------- |
| Cpu, Memory & other peripherals | Only CPU (external components required) |
| Compact and Efficient           | Powerful and Flexible                   |
| Used in embedded Devices        | Used in personal computers              |

# Exercise 
### RISC to CISC
With CISC, the instruction set will be more complex with multi-cycle variable length instructions. Overall performance may be lower.

### Processor Architecture Usage
Microprocessors are designed for performance and flexibility hence use von Neumann. Microcontrollers are designed for real-time control tasks hence use Harvard.

### CISC vs RISC (Cost)
RISC is economical as hardware is cheaper than software. CISC would require implementing more functions in software which is more expensive. 

### Simulator vs Emulator
Simulator models the processor software execution. Emulator models the complete hardware including I/O.

**Simulators** mimic the basic behaviors of a real device but doesn’t necessarily follow all the rules of the real environment. Speed and convenience given precedence over accuracy.  
**Emulator** attempts to mimic all of the hardware features of a production environment and software features.

### Data bus >> Address bus allowed?
8-bit address bus and 32-bit data bus is not possible, as the address bus limits the memory space accessible. 32-bit address bus and 16-bit data bus is possible - the processor will just not utilize the full width of the data bus.