# Questions
### How does the Harvard architecture help to speed up interrupt processing?

The Harvard architecture has separate instruction and data buses, allowing fetch of interrupt vector while current instruction is executing. This reduces latency.

### What are the similarities and differences between system exceptions and external interrupts?

- **Similarities**
	- Both cause context save and transfer to handler code
	- Prioritized handling

- **Differences**
	- Exceptions are synchronous, interrupts asynchronous
	- Exceptions originate within processor, interrupts external to processor
	- Some exceptions have fixed priority

### What are different interrupt states?
- Pending - asserted but not actively being serviced
- Active - being serviced by processor
- Inactive - not asserted and not pending

### Which system exceptions have fixed priority?
Reset, NMI, and Hard Fault have fixed priorities.

### Is it possible to assign the same priority, to an external interrupt, as that of Hard Fault or NMI?
No, Hard Fault and NMI have negative fixed priorities below all configurable priorities.

### What are the minimum and maximum number of priority levels supported by Cortex-M3/M4 based processor?
Min: 3 priority bits -> 8 levels Max: 8 priority bits -> 256 levels

### For less than 8-bit priority, why do we use the most significant bits of priority register?
The MSBs correspond to the higher priority levels. Using MSBs ensures proper priority order.

### If the BASEPRI register is configured with a value of 3, then what are the priorities of possible interrupt sources?
Priorities 0-3 will be masked. Only priorities 4-7 can preempt.

### What is the default memory location of the interrupt vector table (IVT)? Can IVT be moved to data memory region?
Default is start of flash memory. Yes, IVT can be relocated using VTOR register.

### What will happen if the two interrupt service routines, in the vector table, are swapped?
The wrong ISR will execute when the interrupt occurs. This can cause errors.

# Exercise
### When an interrupt occurs, which registers are pushed on to the stack? Are those registers pushed automatically or is the application programmer responsible for that?
xPSR, PC, LR, R12, R3-R0 are automatically pushed by hardware.

### On the occurrence of an interrupt, certain registers are pushed onto the stack. Which stack (process or main) is used for that purpose?
The main stack pointer (MSP) is used.

### If the interrupt occurs during the execution of an instruction, then did the execution of that instruction complete or terminate before execution of the ISR?
No, the instruction is aborted and its execution continues after the ISR.

### What is the special use of register LR in handling the interrupts?
LR contains the return address to resume after ISR completes.

### Under what conditions is the interrupt latency minimized?
When back-to-back interrupts cause tail-chaining.

### How does tail-chaining reduce interrupt latency?
Avoids unnecessary context restore when servicing back-to-back interrupts.

### If there are eight group priorities, then what is the maximum number of sub-priority levels in each group?
256/8 = 32 sub-priority levels per group.



### When an interrupt occurs, it is expected that a corresponding ISR will be executed to generate system response. List at least four interrupt configuration steps that should be performed to ensure the execution of ISR.
- Enable the interrupt source using NVIC_EnableIRQ()
- Set the priority of the interrupt using NVIC_SetPriority()
- Write the interrupt service routine (ISR)
- Set the interrupt vector in the vector table to point to the ISR

### While executing an ISR, is it possible to tell that this ISR has put on hold the execution of the user application program or another ISR of lower priority?
Yes, the xPSR register contains information about the interrupted context. We can check xPSR to determine if the ISR interrupted user mode or another ISR.

### Based on the steps performed by the hardware in response to an interrupt, estimate the delay (in terms of clock cycles) from the occurrence of an interrupt to the execution of the first instruction inside the corresponding ISR. It can be assumed that no other interrupt (of higher priority) has occurred during this time.
The steps performed by hardware include:
- Saving context (xPSR, PC, LR, R12, R3-R0) - 8 cycles
- Fetch first ISR instruction - 1 cycle
- Decode and execute first ISR instruction - 1+ cycles

So the minimum interrupt latency is around 10 - 12 cycles.

### Why are there so many interrupts supported by a microcontroller? Look into two real embedded systems around you and list different interrupts that each system requires.
Microcontrollers need to handle many different types of events and peripherals. For example, a typical embedded system may require:
- External interrupts from sensors
- Timer interrupts for scheduling tasks
- UART interrupts for serial communication
- ADC interrupts for analog to digital conversions
- and more...

### Why do some of the interrupts have fixed priority while priority of others can be programmed? Justify your answer with real-life examples. Can something go wrong if we allow a fixed priority interrupt to become a programmable priority interrupt?
Some critical interrupts like memory faults need to have fixed high priority to handle errors. For example, HardFault needs fixed high priority.

For other interrupts like ADC, timers etc priority can be programmed based on application needs.

Making a fixed high priority interrupt programmable can be dangerous. For example, if HardFault priority could be lowered, a fault may never get handled.

### A Cortex-M microcontroller supports negative values for the priority of some system exceptions. Justify the need to use negative priorities.
Negative priorities allow system exceptions to always take precedence over regular interrupts. This ensures critical exceptions like faults are handled immediately.

### Discuss the differences between local and global mechanisms available on Cortex-M for masking interrupts.
Global masking disables all interrupts unconditionally. Local masking using BASEPRI can disable interrupts below a programmable priority threshold.

Global masking is more heavy handed. Local masking allows flexibility to disable only lower priority interrupts.

### What is interrupt latency? What are its two main components? How does Cortex-M improve the interrupt handling time by reducing interrupt latency?
Interrupt latency is the time from interrupt assertion to start of ISR. It has two main components:
- Context saving time
- Instruction fetch and decode time

Cortex-M reduces latency using:
- Fast context saving of only necessary registers
- Tail-chaining to avoid unnecessary context restore

### A Cortex-M based microcontroller is configured to enable three interrupts with associated priorities. Let source A be assigned priority 1 (highest), while sources B and C be assigned, respectively, priority 3 and 6. Now consider the scenario where interrupt from source C suspends the execution of application program and its ISR is being executed. While its ISR is not finished yet, the interrupts from sources A, B, and C occur and require servicing. Describe the sequence in which these interrupts will be handled by the processor until the application program is resumed. You can assume that no further interrupts occur during this phase.
The interrupt handling sequence will be:
1. ISR C executing
2. Interrupt A occurs -> ISR C pending, start ISR A (priority 1)
3. Interrupt B occurs -> ISR A continues
4. Interrupt C occurs -> ISR A continues
5. ISR A completes and returns
6. Resume pending ISR C
7. ISR C completes and returns
8. Resume application program
So the interrupts will be handled in order A, C based on priority.

### Consider a scenario where n multiple interrupts are configured with m different priority levels. What will be minimum stack size required, keeping in view the interrupt nesting possibility, for the following two cases:
11. n > m,
12. n < m.
Minimum stack size is independent of n and m. It depends only on number of priority levels and registers pushed per interrupt.
For Cortex-M3:
- 16 priority levels
- 8 registers pushed per interrupt
Minimum stack = 16 * 8 * 4 = 512 bytes
So minimum stack is 512 bytes for both cases.