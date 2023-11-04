### What are the uses of open-drain functionality, when it is available on a GPIO pin?
The open-drain functionality can be used for interfacing with external devices that require wired-AND logic or open-collector outputs. It allows multiple devices to share a common bus line.

### Name different communication and timing peripherals that are available on TM4C123.
Communication peripherals on TM4C123 include UART, I2C, SSI, CAN, USB. Timing peripherals include general purpose timers, watchdog timers, RTC.

### What debug/programming interfaces are available on TM4C123?
TM4C123 has SWD, JTAG and SSI debugging/programming interfaces.

### What are four basic hardware connections that are essential for proper functioning of a microcontroller?
The four basic hardware connections are: power supply, clock source, reset signal, and debug interface. 

### How much RAM and flash (on chip) memories are integrated in TM4C123 and what are their address ranges?
TM4C123 has 256 KB flash and 32 KB SRAM. The flash range is 0x0000_0000 - 0x0003_FFFF and SRAM range is 0x2000_0000 - 0x2000_7FFF.

### List four configuration steps required to use a microcontroller pin for GPIO purpose.  
The four configuration steps are: 1) Configure system clock 2) Configure pin for digital function 3) Configure pin direction 4) Enable GPIO port clock.

### Why does the GPIO data register have more than one address assigned to it? This is in contrast to other registers, which are assigned only one address.
The GPIO data register is aliased to support atomic bit manipulation using the bit-band region. This allows each bit to be accessed using a unique address. 

### What is the disadvantage of special data register masking supported by TM4C123 microcontroller?
The disadvantage is that it requires more instructions compared to straightforward masking in software.

### When a GPIO pin is to be used for an alternate functionality, which two registers should be configured for this purpose?
The GPIOAMSEL and GPIOPCTL registers should be configured.

The LEDs in Figure 8.10 are turned on when a logic high signal is applied on the corresponding GPIO pin. Now we are interested in turning on the LED when a logic low signal is applied. For that purpose, redraw Figure 8.10 for LED wiring so that a logic low signal on the corresponding GPIO turns on the LED.

The LED anode should be connected to Vcc instead of ground. The cathode should be connected to the GPIO pin through a current limiting resistor. A logic low on the GPIO will turn on the LED in this configuration.

### While defining register labels in a C program, why do we use the ‘volatile’ key word?
The 'volatile' keyword informs the compiler that the value of the register can change unexpectedly. This prevents unwanted compiler optimizations on these registers.

### When the GPIO pins have limited current sourcing but large current sinking capability, which seven-segment display (common anode or common cathode) would be preferred?
A common cathode seven-segment display would be preferred in this case.

### We are interested in using a keypad interface with the option of multiple simultaneous key presses. Among the three different types of keypad interfaces discussed in this chapter, which one is more suitable for this case?
The matrix keypad interface can detect multiple simultaneous key presses and would be suitable in this case.