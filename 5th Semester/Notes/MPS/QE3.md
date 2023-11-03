Okay, here are the numbered questions:

How does the Harvard architecture help to speed up interrupt processing?

What are the similarities and differences between system exceptions and external interrupts? 

What are different interrupt states?

Which system exceptions have fixed priority?

Is it possible to assign the same priority, to an external interrupt, as that of Hard Fault or NMI?

What are the minimum and maximum number of priority levels supported by Cortex-M3/M4 based processor?

For less than 8-bit priority, why do we use the most significant bits of priority register? 

If the BASEPRI register is configured with a value of 3, then what are the priorities of possible interrupt sources?

What is the default memory location of the interrupt vector table (IVT)? Can IVT be moved to data memory region?

 What will happen if the two interrupt service routines, in the vector table, are swapped?

 When an interrupt occurs, which registers are pushed on to the stack? Are those registers pushed automatically or is the application programmer responsible for that?

 On the occurrence of an interrupt, certain registers are pushed onto the stack. Which stack (process or main) is used for that purpose? 

 If the interrupt occurs during the execution of an instruction, then did the execution of that instruction complete or terminate before execution of the ISR?

 What is the special use of register LR in handling the interrupts? 

 Under what conditions is the interrupt latency minimized? 

 How does tail-chaining reduce interrupt latency?

 If there are eight group priorities, then what is the maximum number of sub-priority levels in each group?