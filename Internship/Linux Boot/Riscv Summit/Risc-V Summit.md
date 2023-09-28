# 1. Boot-flow
## Rom reset 
Called so because it is loaded from ROM, present on the board.
### Functions 
- Power on reset
- Clock set

## 2. Loader Stage (1st Stage BL)
### Functions
 - DDR initialization
 - Loading next stages:
	 - Runtime
	 - Proper Bootloader
### Examples
- Bios / UEFI
	- x86 
- Uboot SPL
	- Embedded System
- Core Boot
	- Chromebook


## 3. Runtime
Sometimes combined into UEFI 
- Run from on chip SRAM or DDR 
### Function
- Security components of the bootflow.
- Runtime services for OS.
Runtime services (required for OS talk to higher privilege mode) are after system boot, Boot services are before boot (specific to UEFI).


## 4. Bootloader
### Function
- Loading kernel image from media
- 