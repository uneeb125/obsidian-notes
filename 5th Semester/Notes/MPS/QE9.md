# Question
### 9.1 What is the key difference between blind cycle and busy wait synchronization?
The key difference is that blind cycle synchronization waits for a fixed amount of time, while busy wait synchronization continuously checks the status of the device.

### 9.2 How does periodic polling based synchronization differ from continuous polling synchronization?
Periodic polling checks the status at regular intervals, while continuous polling keeps checking the status repeatedly.

### 9.3 Are external interrupts synchronous or asynchronous exceptions? 
External interrupts are asynchronous exceptions.

### 9.4 Assume that the starting address for the interrupt vector table is 0x00000000. What will be the interrupt service routine address of IRQ30?
0x000000BC

### 9.5 What are different configuration levels to enable an interrupt from a peripheral device?
The different configuration levels are:
- Processor level
- NVIC level  
- Device level

### 9.6 How does the priority configuration for system exceptions (with programmable priority) differ from that of interrupt requests (IRQs)?
System exceptions have fixed priority levels, while IRQ priorities can be programmed.  

### 9.7 Is it necessary to list the addresses of all interrupt service routines (ISRs) in the interrupt vector table?
No, only the addresses of implemented ISRs need to be listed.

### 9.8 Show the interrupt vector table entries, if only ISRs for exceptions 1-3 and IRQ 2 are implemented.
```
0x00000004
0x00000008
0x0000000C 
0x00000010
```

### 9.9 What different device level configurations are required to enable an interrupt from a peripheral device? 
Device level configuration includes enabling the clock, initializing the GPIO, and configuring the interrupt enable register.

### 9.10 When a GPIO is used as a source of an external interrupt, then how can it be configured as level or edge triggered? 
It can be configured in the GPIO interrupt configuration register. 

### 9.11 Why is it necessary to clear the interrupt flag before exiting the ISR?
To prevent the interrupt from recurring immediately after exiting the ISR.

### 9.12 How can we mask interrupts from different port pins of port A using a single register configuration? How can it be achieved for multiple GPIO ports and again using a single register?
Use the GPIO port A interrupt mask register. Use the NVIC interrupt mask register for multiple GPIO ports.


# Exercise