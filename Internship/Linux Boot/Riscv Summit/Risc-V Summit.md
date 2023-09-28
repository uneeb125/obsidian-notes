# General Boot-flow
## 1. Rom Reset 
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
### Examples
- Grub 
- Linux Boot
- Uboot (embedded)
### Function
- Loading kernel image from media

## 5. Kernel
## 6. OS
### Examples
- Linux
- OpenBSD
- NetBSD



# ARM64 Boot-flow
## 1. Rom Reset
## 2. Core Boot or Uboot SPL
Loads both ATF and Uboot images
- Falcon mode
	Let Uboot SPL Boot OS directly.
	- Smaller embedded
	- Faster Boot
## 3. Arm Trusted Firmware
## 4. Uboot
- Falcon mode
	Let Uboot SPL Boot OS directly.
	- Smaller embedded
	- Faster Boot

# RISC-V Boot-flow
![[Riscv_bootflow.jpg]]
## Zero Stage BL (Rom Reset)
## 1st Stage BL 
## 2nd Stage

[Specific boot] (https://youtu.be/sPjtvqfGjnY?si=pro7ON3dgbmv0ebm&t=749)

![[Riscv_bootflow.jpg]]



