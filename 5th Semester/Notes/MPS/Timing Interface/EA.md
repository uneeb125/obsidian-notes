### Exercise 10.1:
**Advantages of Using an Internal Oscillator:**
1. **Cost-Effectiveness:** Internal oscillators eliminate the need for an external component, reducing overall system cost.
2. **Space Saving:** Internal oscillators save space on the PCB compared to external components.
3. **Ease of Integration:** Internal oscillators are integrated into the microcontroller, simplifying design and reducing external dependencies.

**Disadvantages of Using an Internal Oscillator:**
1. **Accuracy:** Internal oscillators may be less accurate than external ones, affecting overall timing precision.
2. **Limited Frequency Options:** External oscillators often provide more frequency choices than internal ones.
3. **Temperature Sensitivity:** Internal oscillators can be more sensitive to temperature variations, affecting stability.

### Exercise 10.2:
```c
#include <stdint.h>
#include "tm4c123gh6pm.h"

int main(void) {
    // Enable the PLL and set the system clock to 64 MHz
    SYSCTL_RCC_R |= SYSCTL_RCC_BYPASS;      // Bypass PLL and system clock divider
    SYSCTL_RCC_R &= ~SYSCTL_RCC_PWRDN;      // Enable PLL
    SYSCTL_RCC_R &= ~SYSCTL_RCC_OSCSRC_M;   // Clear oscillator source bits
    SYSCTL_RCC_R += SYSCTL_RCC_OSCSRC_MAIN; // Set main oscillator source
    SYSCTL_RCC_R &= ~SYSCTL_RCC_XTAL_M;     // Clear crystal value bits
    SYSCTL_RCC_R += (0x15 << SYSCTL_RCC_XTAL_S); // Set crystal value to 16 MHz
    SYSCTL_RCC_R &= ~SYSCTL_RCC_SYSDIV_M;   // Clear system clock divider
    SYSCTL_RCC_R += (0x3 << SYSCTL_RCC_SYSDIV_S); // Set system clock divider to achieve 64 MHz

    // Wait for the PLL to lock
    while (!(SYSCTL_RIS_R & SYSCTL_RIS_PLLLRIS));

    // Enable the GPIO port that is used for LED and configure the LED pins as outputs
    SYSCTL_RCGC2_R |= SYSCTL_RCGC2_GPIOF;   // Enable Port F GPIO
    GPIO_PORTF_DIR_R = 0x0E;                // PF1, PF2, and PF3 are outputs
    GPIO_PORTF_DEN_R = 0x0E;                // Enable digital function on PF1, PF2, and PF3

    while (1) {
        // Your code here
    }
}
```

This program configures the TM4C123 clock frequency to 64 MHz by enabling the PLL and adjusting the necessary system clock settings.

### Exercise 10.3:
**(a) Count Down Mode:**
```c
#include <stdint.h>
#include "tm4c123gh6pm. h"

#define TIMER_FREQUENCY 16000000  // Timer clock frequency in Hz
#define DESIRED_INTERVAL 1000     // Desired interval in microseconds (1 ms)

int main (void) {
    // Calculate the reload value for count down mode
    uint32_t reload_value = (TIMER_FREQUENCY * DESIRED_INTERVAL) / 1000000 - 1;

    // Your code here

    while (1) {
        // Your code here
    }
}
```

**(b) Count Up Mode:**
```c
#include <stdint.h>
#include "tm4c123gh6pm. h"

#define TIMER_FREQUENCY 16000000  // Timer clock frequency in Hz
#define DESIRED_INTERVAL 1000     // Desired interval in microseconds (1 ms)

int main (void) {
    // Calculate the reload value for count up mode
    uint32_t reload_value = TIMER_FREQUENCY / 1000 * DESIRED_INTERVAL - 1;

    // Your code here

    while (1) {
        // Your code here
    }
}
```

These programs calculate the appropriate reload value for generating a timer interrupt every 1 ms in both count down and count up modes.

### Exercise 10.4:
To generate an interrupt after every fifth event, configure the timer in **Capture Mode** with a **Capture Match Value** of 5.

### Exercise 10.5:
```c
#include <stdint.h>
#include "tm4c123gh6pm. h"

#define SYSTICK_FREQUENCY 16000000  // Systick timer frequency in Hz
#define DESIRED_FREQUENCY 1000      // Desired output frequency in Hz

int main (void) {
    // Calculate the reload value for a 1 kHz square wave
    uint32_t reload_value = SYSTICK_FREQUENCY / (2 * DESIRED_FREQUENCY) - 1;

    // Your code here

    while (1) {
        // Your code here
    }
}
```

This program generates a 1 kHz square wave on pin PA5 using the Systick timer.

### Exercise 10.6:
```c
#include <stdint.h>
#include "tm4c123gh6pm. h"

#define TIMER_FREQUENCY 16000000  // Timer clock frequency in Hz
#define DESIRED_INTERVAL 100000   // Desired interval in microseconds (100 ms)

int main (void) {
    // Calculate the reload value for a 100 ms interval
    uint32_t reload_value = (TIMER_FREQUENCY * DESIRED_INTERVAL) / 1000000 - 1;

    // Your code here

    while (1) {
        // Your code here
    }
}
```

This program calculates the reload value for generating 100 ms intervals using a 16-bit down counter based timer.

### Exercise 10.7:
```c
#include <stdint.h>
#include "tm4c123gh6pm. h"

#define CLOCK_FREQUENCY 1000000  // Cortex-M processor clock frequency in Hz
#define SIGNAL_DURATION 15000    // Pedestrian signal duration in microseconds (15 s)

void SysTick_Handler (void) {
    // Your code here to handle the interrupt
}

int main (void) {
    // Your code here to configure GPIO and initialize variables

    // Configure the Systick timer for a 1 MHz clock frequency
    NVIC_ST_CTRL_R = 0;                   // Disable SysTick during setup
    NVIC_ST_RELOAD_R = CLOCK_FREQUENCY - 1; // Set reload value for a 1 us interval
    NVIC_ST_CTRL_R = NVIC_ST_CTRL_ENABLE + NVIC_ST_CTRL_CLK_SRC; // Enable SysTick with processor clock

    while (1) {
        // Your code here to implement the functionality
    }
}
```

This program implements the pedestrian signal crossing functionality using an ARM Cortex-M processor running at a 1 MHz clock.

### Exercise 10.8:
The maximum frequency that can be reliably measured using time period-based frequency measurement is given by the reciprocal of the measurement interval. Assuming a 1% error tolerance, the maximum frequency (f_max) can be calculated using the formula:

\[ f_{max} = \frac{1}{2 \times \text{Measurement Interval} \times 0.01} \]

### Exercise 10.9:
To measure the interrupt entry latency (IEL) using the SysTick timer:
1. Disable interrupts globally.
2. Record the current value of the SysTick timer.
3. Generate a software interrupt (e.g., `NVIC_INT_CTRL_R |= NVIC_INT_CTRL_PEND_SV`).
4. In

 the interrupt service routine, record the current value of the SysTick timer.
5. Calculate the difference between the two recorded values to obtain the IEL.

### Exercise 10.10:
To configure the priority of the Systick timer to 5 on TM4C123:
```c
NVIC_SYS_PRI3_R = (NVIC_SYS_PRI3_R & ~NVIC_SYS_PRI3_TICK_M) | (5 << NVIC_SYS_PRI3_TICK_S);
```
The default priority of the Systick timer is usually the lowest.

### Exercise 10.11:
To measure interrupt exit latency:
1. Record the current value of the SysTick timer before the ISR code.
2. Execute the ISR code.
3. Record the current value of the SysTick timer after the ISR code.
4. Calculate the difference between the two recorded values to obtain the interrupt exit latency.

### Exercise 10.12:
The exercise involves implementing Frequency Shift Keying (FSK) communication using timer module (s). Specific details on the number of timers, operating modes, and GPIO configurations would depend on the chosen approach. The high-level steps include selecting a timer mode suitable for FSK, configuring the timer, and handling interrupts to toggle the frequency based on the transmitted data.

### Exercise 10.13:
The maximum time interval before a 32-bit timer overflows is given by:
\[ \text{Max Time Interval} = \frac{2^{32} - 1}{\text{Timer Frequency}} \]
Substitute the values to find the result.

### Exercise 10.14:
```c
#include <stdint.h>
#include "tm4c123gh6pm. h"

void configureTimer (uint32_t frequency) {
    // Your code to configure the timer for variable frequency
}

int main (void) {
    uint32_t frequency = 10000;  // Starting frequency in Hz

    configureTimer (frequency);

    while (1) {
        // Your code to adjust frequency as needed
    }
}
```

This program generates a variable frequency signal using the timer module, with the frequency varying from 10 kHz to 20 kHz in 1 kHz steps.

### Exercise 10.15:
The maximum achievable PWM resolution (number of bits) can be calculated using the formula:
\[ \text{Resolution} = \frac{\text{Timer Frequency}}{\text{Desired PWM Frequency}} \]

### Exercise 10.16:
```c
#include <stdint.h>
#include "tm4c123gh6pm. h"

int main (void) {
    // Configure the timer for PWM generation with a 70% duty cycle
    // and negative half cycle produced first followed by positive half cycle.

    while (1) {
        // Your code here
    }
}
```
This exercise involves configuring the timer module to generate a PWM signal with a 70% duty cycle, where the negative half cycle is produced first followed by the positive half cycle. The specific configuration details depend on the timer module used and the desired PWM characteristics.