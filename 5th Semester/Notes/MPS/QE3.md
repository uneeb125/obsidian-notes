1. When an interrupt occurs, it is expected that a corresponding ISR will be executed to generate system response. List at least four interrupt configuration steps that should be performed to ensure the execution of ISR.

- Enable the interrupt source using NVIC_EnableIRQ()
- Set the priority of the interrupt using NVIC_SetPriority()
- Write the interrupt service routine (ISR)
- Set the interrupt vector in the vector table to point to the ISR

2. While executing an ISR, is it possible to tell that this ISR has put on hold the execution of the user application program or another ISR of lower priority?

Yes, the xPSR register contains information about the interrupted context. We can check xPSR to determine if the ISR interrupted user mode or another ISR.

3. Based on the steps performed by the hardware in response to an interrupt, estimate the delay (in terms of clock cycles) from the occurrence of an interrupt to the execution of the first instruction inside the corresponding ISR. It can be assumed that no other interrupt (of higher priority) has occurred during this time.

The steps performed by hardware include:

- Saving context (xPSR, PC, LR, R12, R3-R0) - 8 cycles
- Fetch first ISR instruction - 1 cycle
- Decode and execute first ISR instruction - 1+ cycles

So the minimum interrupt latency is around 10 - 12 cycles.

4. Why are there so many interrupts supported by a microcontroller? Look into two real embedded systems around you and list different interrupts that each system requires.

Microcontrollers need to handle many different types of events and peripherals. For example, a typical embedded system may require:

- External interrupts from sensors
- Timer interrupts for scheduling tasks
- UART interrupts for serial communication
- ADC interrupts for analog to digital conversions
- and more...

5. Why do some of the interrupts have fixed priority while priority of others can be programmed? Justify your answer with real-life examples. Can something go wrong if we allow a fixed priority interrupt to become a programmable priority interrupt?

Some critical interrupts like memory faults need to have fixed high priority to handle errors. For example, HardFault needs fixed high priority.

For other interrupts like ADC, timers etc priority can be programmed based on application needs.

Making a fixed high priority interrupt programmable can be dangerous. For example, if HardFault priority could be lowered, a fault may never get handled.

6. A Cortex-M microcontroller supports negative values for the priority of some system exceptions. Justify the need to use negative priorities.

Negative priorities allow system exceptions to always take precedence over regular interrupts. This ensures critical exceptions like faults are handled immediately.

7. Discuss the differences between local and global mechanisms available on Cortex-M for masking interrupts.

Global masking disables all interrupts unconditionally. Local masking using BASEPRI can disable interrupts below a programmable priority threshold.

Global masking is more heavy handed. Local masking allows flexibility to disable only lower priority interrupts.

8. What is interrupt latency? What are its two main components? How does Cortex-M improve the interrupt handling time by reducing interrupt latency?

Interrupt latency is the time from interrupt assertion to start of ISR. It has two main components:

- Context saving time
- Instruction fetch and decode time

Cortex-M reduces latency using:

- Fast context saving of only necessary registers
- Tail-chaining to avoid unnecessary context restore

9. A Cortex-M based microcontroller is configured to enable three interrupts with associated priorities. Let source A be assigned priority 1 (highest), while sources B and C be assigned, respectively, priority 3 and 6. Now consider the scenario where interrupt from source C suspends the execution of application program and its ISR is being executed. While its ISR is not finished yet, the interrupts from sources A, B, and C occur and require servicing. Describe the sequence in which these interrupts will be handled by the processor until the application program is resumed. You can assume that no further interrupts occur during this phase.

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

10. Consider a scenario where n multiple interrupts are configured with m different priority levels. What will be minimum stack size required, keeping in view the interrupt nesting possibility, for the following two cases:
11. n > m,
12. n < m.

Minimum stack size is independent of n and m. It depends only on number of priority levels and registers pushed per interrupt.

For Cortex-M3:

- 16 priority levels
- 8 registers pushed per interrupt

Minimum stack = 16 * 8 * 4 = 512 bytes

So minimum stack is 512 bytes for both cases.