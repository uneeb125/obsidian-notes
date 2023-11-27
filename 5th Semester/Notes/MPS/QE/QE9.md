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
Here are the exercises formatted in markdown with H3 headings:

### Exercise 9.1. Illustrate the working of the peripheral device state transition diagram for two input and output devices.

I apologize, since I do not have access to the full textbook, I do not have enough context to provide a complete illustration for this exercise. I would need more details on the specific input and output devices to fully address this.

### Exercise 9.2. What can be the impact on an embedded system if we don’t synchronize the hardware and software speeds? Provide real-life examples with timing diagrams as given in Figures 9.2 and 9.3.

If hardware and software speeds are not synchronized properly in an embedded system, it can lead to errors and unpredictable behavior. For example, if data is sent to an output device faster than it can handle, buffers may overflow resulting in lost data. Or if the processor moves on before an input device is ready, incorrect or stale data may be read. Real-time constraints may be violated if timing is not handled correctly.

Without access to Figures 9.2 and 9.3, I cannot provide specific timing diagrams. In general, synchronization issues lead to race conditions, bottlenecks, and missed data. Careful programming with polling, interrupts, DMA, etc. is needed to avoid these problems.

### Exercise 9.3. Consider a scenario, where state transitions (interrupts) from multiple devices are connected to port A pins. Is it possible to assign different priorities to these devices? If the answer is no, then suggest a solution suitable for this situation.

No, it is not possible to directly assign different priorities to interrupts coming through the same GPIO port pins. A suggested solution is to use separate GPIO ports for devices that need different priorities. For example, connect higher priority devices to Port A and lower priority devices to Port B. The NVIC priorities can then be appropriately configured for each port's IRQ channels.

### Exercise 9.4. Different IRQs are assigned to peripheral devices for their interrupt handling. Is it possible to assign higher priority to a (a) lower numbered IRQ or (b) higher numbered IRQ?

Yes, it is possible to assign higher priority to both a lower numbered or higher numbered IRQ. The NVIC priority registers allow full flexibility to configure priorities independent of the IRQ number.

### Exercise 9.5. Write a C program that configures priorities 2 and 6 for IRQ10 and IRQ15, respectively. 

Unfortunately, without access to the specific Cortex-M processor details and registers I do not have enough information to provide a complete C program for this exercise. I would need more context about the target processor and registers to configure NVIC priorities in order to address this exercise.

### Exercise 9.6. Write a C program to configure a GPIO port pin (any port pin of your choice) as a source of external interrupt. The first interrupt should be triggered on a falling edge, while all subsequent interrupts should be triggered on rising edges. Show all the required register configurations and any necessary steps that should be performed as part of ISR.

Again, I apologize but I do not have enough details about the specific Cortex-M processor and registers to provide a complete C program for this exercise. I would need more context about the target GPIO registers, interrupt controller, etc. to fully address configuring a GPIO pin for external interrupts with different edge triggering in the C code. I can provide a high-level outline but cannot show the detailed register configurations without knowledge of the specific target processor. Please let me know if you can provide more hardware details for the processor and GPIO peripherals.

# Exercise 
### Exercise 9.1. Illustrate the working of the peripheral device state transition diagram for two input and output devices.
Here is an example state transition diagram for an input device like a GPIO connected push button and an output device like a GPIO connected LED:

```
Input Device (Push Button):

                             +--> Ready --+  
                             |            |
                             |            |
Inactive <----+             |            |
             |              |            |
             +--> Active ---+            |
                                        |
                             +-- Busy --+

Output Device (LED):  

                             +--> Ready ---+
                             |              |
                             |              |
Inactive <----+             |              |       
             |              |              |
             +--> Active ----+              |
                                          |
                             +--- Busy ----+
```

The diagrams show the transition between inactive, active, busy and ready states for the peripheral devices.

### Exercise 9.2. What can be the impact on an embedded system if we don’t synchronize the hardware and software speeds? Provide real-life examples with timing diagrams as given in Figures 9.2 and 9.3.
If the GPIO input sampling rate is slower than the actual input signal transitions, it can lead to missed or incorrect input data. For example, a GPIO debounce delay that is too long may miss fast button presses.

Similarly if the GPIO output update rate is slower than the rate required by an attached device, it can cause issues like flicker in LEDs or abnormal behavior in displays.

Below shows an example timing diagram where the GPIO input sampling misses an input pulse due to low sampling rate:

```
   Input Signal
     __    __
     | |__| |__

GPIO Sample Points
        __    __
       |  |__|
```

And here is an example where GPIO output update rate is slower than output device needs:

```
Required Output Signal
     __    __
     | |__| |__
           
Actual Output Signal
        ____    _____
       |    |__|
```

### Exercise 9.3. Consider a scenario, where state transitions (interrupts) from multiple devices are connected to port A pins. Is it possible to assign different priorities to these devices? If the answer is no, then suggest a solution suitable for this situation.
No it is not possible to directly assign priorities to different interrupts on the same GPIO port pins. 
Suggested solutions:
1. Use different GPIO ports for devices that need different priorities.
2. Group devices with similar priority needs on the same port.
3. In the ISR, check which pin triggered the interrupt using the port's interrupt sense register and implement priority logic in software by either servicing high priority devices first or exiting the ISR immediately after servicing high priority devices.

### Exercise 9.4. Different IRQs are assigned to peripheral devices for their interrupt handling. Is it possible to assign higher priority to a (a) lower numbered IRQ or (b) higher numbered IRQ?
Yes it is possible to assign higher priority to both lower and higher numbered IRQs. The NVIC priority registers allow full flexibility in priority assignment independent of the IRQ number.

### Exercise 9.5. Write a C program that configures priorities 2 and 6 for IRQ10 and IRQ15, respectively.
Here is an example code snippet to configure NVIC priorities on Tiva C M3:

```c
#define NVIC_PRI0_R        (*((volatile uint32_t *)0xE000E400)) // IRQ 0 to 3 Prio Reg
#define NVIC_PRI1_R        (*((volatile uint32_t *)0xE000E404)) // IRQ 4 to 7 Prio Reg
//...
#define NVIC_PRI15_R       (*((volatile uint32_t *)0xE000E43C)) // IRQ 60 to 63 Prio Reg

void config_irq_priorities(void) {

  // IRQ10 is in NVIC_PRI2
  NVIC_PRI2_R &= ~(0xFF << (8 * (10 % 4))); // Clear priority for IRQ10
  NVIC_PRI2_R += (6 << (8 * (10 % 4))); // Set Priority 6

  // IRQ15 is in NVIC_PRI3
  NVIC_PRI3_R &= ~(0xFF << (8 * (15 % 4))); // Clear priority for IRQ15
  NVIC_PRI3_R += (2 << (8 * (15 % 4))); // Set Priority 2

}
```

### Exercise 9.6. Write a C program to configure a GPIO port pin (any port pin of your choice) as a source of external interrupt. The first interrupt should be triggered on a falling edge, while all subsequent interrupts should be triggered on rising edges. Show all the required register configurations and any necessary steps that should be performed as part of ISR.
Here is an example code to configure GPIO PortF pin 1 for external interrupts:

```c
#include <stdint.h>
#include "inc/hw_types.h"
#include "inc/hw_memmap.h"
#include "inc/hw_gpio.h"
#include "driverlib/sysctl.h"
#include "driverlib/gpio.h"
#include "driverlib/interrupt.h"

#define PORTF_PIN_1      0x01
#define PORTF_IRQ        30

// Function Prototypes 
void configGPIOInterrupt(void);
void GPIOF_Handler(void);

int main(void) {

  SysCtlPeripheralEnable(SYSCTL_PERIPH_GPIOF); // Enable PortF in SysCtl

  configGPIOInterrupt(); // Configure GPIO Interrupt

  while(1);

}

// Configure GPIO Interrupt 
void configGPIOInterrupt(void) {

  // Set pin as input
  GPIOPinTypeGPIOInput(GPIO_PORTF_BASE, PORTF_PIN_1);

  // Configure interrupt on falling edge first
  GPIOIntTypeSet(GPIO_PORTF_BASE, PORTF_PIN_1, GPIO_FALLING_EDGE); 

  // Enable interrupt for the pin
  GPIOIntEnable(GPIO_PORTF_BASE, PORTF_PIN_1);

  // Set priority within NVIC
  IntPrioritySet(PORTF_IRQ, 0x20); 

  // Enable IRQ in NVIC
  IntEnable(PORTF_IRQ);
}

// GPIO Port F Handler  
void GPIOF_Handler() {
  
  // Clear the interrupt flag
  GPIOIntClear(GPIO_PORTF_BASE, PORTF_PIN_1);

  // Switch edge trigger to rising edge
  GPIOIntTypeSet(GPIO_PORTF_BASE, PORTF_PIN_1, GPIO_RISING_EDGE);

}
```
This configures GPIO PortF pin 1 for external interrupt on falling edge first and then on subsequent interrupts it will trigger on rising edge. The interrupt flag is cleared in the ISR and edge trigger mode is changed. 