# Build requirements
## 3 requirements
1. Bootloaders (bios???)
	- Hardware recognition and diagnosis
## Types/Levels of bootloader
### Level Zero
- Configurable using hardware switches (jumpers).
- Built in to processor. or outside as a chip.
- Required for arm.
- Loads the first level bootloader.
	- Example is the bootloader for Raspberry.
- Header footer concept used.

Verilator for Simulated booting without UART.

- Fence flushes all remaining data (dirty data) in DATA cache to be properly written into main memory.
- Next we write to 0x80000000, the level 1 bootloader

### Level One
- Kernel uses the device tree to see what hardware is available.


Possibly next level is uboot.
