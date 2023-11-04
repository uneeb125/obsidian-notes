
### Question 8.1. What are the uses of open-drain functionality, when it is available on a GPIO pin?
The open-drain functionality can be used for interfacing with external devices that require wired-AND logic or open-collector outputs. It allows multiple devices to share a common bus line.

### Question 8.2. Name different communication and timing peripherals that are available on TM4C123.
Communication peripherals on TM4C123 include:
- UART
- I2C  
- SSI
- CAN
- USB
Timing peripherals include: 
- General purpose timers
- Watchdog timers
- RTC

### Question 8.3. What debug/programming interfaces are available on TM4C123?
TM4C123 has the following debug/programming interfaces:
- SWD
- JTAG
- SSI 

### Question 8.4. What are four basic hardware connections that are essential for proper functioning of a microcontroller?
The four basic hardware connections are:
- Power supply
- Clock source
- Reset signal 
- Debug interface

### Question 8.5. How much RAM and flash (on chip) memories are integrated in TM4C123 and what are their address ranges?
TM4C123 has:
- 256 KB flash with address range 0x0000_0000 - 0x0003_FFFF
- 32 KB SRAM with address range 0x2000_0000 - 0x2000_7FFF

### Question 8.6. List four configuration steps required to use a microcontroller pin for GPIO purpose.   
The four configuration steps are:
1. Configure system clock
2. Configure pin for digital function
3. Configure pin direction 
4. Enable GPIO port clock

### Question 8.7. Why does the GPIO data register have more than one address assigned to it? This is in contrast to other registers, which are assigned only one address.
The GPIO data register is aliased to support atomic bit manipulation using the bit-band region. This allows each bit to be accessed using a unique address.

### Question 8.8. What is the disadvantage of special data register masking supported by TM4C123 microcontroller?
The disadvantage is that it requires more instructions compared to straightforward masking in software.

### Question 8.9. When a GPIO pin is to be used for an alternate functionality, which two registers should be configured for this purpose?
The GPIOAMSEL and GPIOPCTL registers should be configured.

### Question 8.10. The LEDs in Figure 8.10 are turned on when a logic high signal is applied on the corresponding GPIO pin. Now we are interested in turning on the LED when a logic low signal is applied. For that purpose, redraw Figure 8.10 for LED wiring so that a logic low signal on the corresponding GPIO turns on the LED.
The LED anode should be connected to Vcc instead of ground. The cathode should be connected to the GPIO pin through a current limiting resistor. A logic low on the GPIO will turn on the LED in this configuration.

### Question 8.11. While defining register labels in a C program, why do we use the ‘volatile’ key word? 
The 'volatile' keyword informs the compiler that the value of the register can change unexpectedly. This prevents unwanted compiler optimizations on these registers.

### Question 8.12. When the GPIO pins have limited current sourcing but large current sinking capability, which seven-segment display (common anode or common cathode) would be preferred?
A common cathode seven-segment display would be preferred in this case.

### Question 8.13. We are interested in using a keypad interface with the option of multiple simultaneous key presses. Among the three different types of keypad interfaces discussed in this chapter, which one is more suitable for this case?
The matrix keypad interface can detect multiple simultaneous key presses and would be suitable in this case.

# Exercise



Exercise 8.1. If any of the other three configuration steps (pin direction, alternate function, or GPIO port clock enable) are done before the system clock configuration, the GPIO registers will be inaccessible and the configuration writes will have no effect. The system clock must be configured first to enable access to the GPIO registers.

Exercise 8.2. 
(a) To update pins 0, 2, and 7 as outputs without affecting other pins, the DATA register address should be 0x40006010. This will access pins 0, 2, and 7 directly.

(b) To read pins 1 and 4 as inputs without read-modify-write, the DATA register address should be 0x40006014. This will access only pins 1 and 4. 

Exercise 8.3. The 4-digit 7-segment display can be interfaced using 10 GPIOs as follows:

- Use 7 GPIOs for the 7-segments and 1 GPIO for decimal point. Drive them low to turn on the segments.

- Use 1 GPIO connected to a demultiplexer like 74HC138. The demultiplexer output will connect to the common cathode of each digit. 

- Use 1 GPIO to control the demultiplexer select lines to enable one digit at a time.

Exercise 8.4. Here is the outline for an efficient matrix keypad scanning algorithm using two scans:

1. Set all column pins as outputs, drive high
2. Set all row pins as inputs 
3. Read row pins, save status

4. Set all row pins as outputs, drive high
5. Set all column pins as inputs
6. Read column pins, save status 

7. Combine saved row and column status to detect key press

Exercise 8.5. Here is the code to configure and write to a 4-bit LCD:

```c
// LCD in 4-bit mode
// Configure LCD for 4-bit mode  
LCD_Command(0x02u); // 4-bit mode
LCD_Command(0x28u); // 2 line, 5x8 font

// Write text 
LCD_Write4bits(0x20u); // Write 'H'
LCD_Write4bits(0x65u); // Write 'e'
LCD_Write4bits(0x6Cu); // Write 'l' 
LCD_Write4bits(0x6Cu); // Write 'l'
LCD_Write4bits(0x6Fu); // Write 'o'
```

Exercise 8.6. Here is the code outline to toggle LEDs using switches with interrupts:

```c
// GPIO and interrupt initialization

void PORTF_Handler() {
  if (SW1 pressed) {
     Toggle PF1 
  }
  if (SW2 pressed) {
     Toggle PF2
  }
}

int main() {

  Enable interrupts
  
  while(1) {
    // Do nothing    
  }

}
```

Exercise 8.7. For a 4-digit display with 2 common anode and 2 common cathode digits:

- For common anode: Anode to Vcc, cathode to GPIO through resistor 
- For common cathode: Cathode to GND, anode to GPIO through resistor

Exercise 8.8. For an n-digit multiplexed 7-segment display, n + 4 GPIOs are required minimum. 

- 7 GPIOs for 7-segments + decimal point
- n GPIOs to enable one digit at a time
- Total = n + 7 GPIOs