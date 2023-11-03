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

