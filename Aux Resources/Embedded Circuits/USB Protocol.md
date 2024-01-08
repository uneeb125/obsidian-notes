# Full Specification
[[usb-20-specification.pdf]]

## Hardware
- Red (V Bus)
- Black (GND)
- Green (D+)
- White (D-)
![[Pasted image 20240109040809.png]]
- Differential used for noise prevention
## States
![[Pasted image 20240109040902.png]]
## Data Transfer (NRZI)
- Non Return to Zero Inverted
- The transitions carry the data
- The **Clock** is determined from the sync section transitions
![[Pasted image 20240109041209.png]]
### Bit Stuffing
- Transition is forced after 6 consecutive non transitions
- Done to maintain the clock
- It is not read as part of the data, is essentially ignored.
## Packet Structure
![[Pasted image 20240109041749.png]]
1. Sync
2. PID
3. DATA
4. EOP
### Types of Packets
#### Token
 ![[Pasted image 20240109041915.png]]
-  Only sent by host, no device allowed to sent on their own
- Initiate communication
##### PIDs
- OUT
- IN
- SETUP
	Similar to out, used for device configuration
All three above are followed by
- 7-bit address
- 4-bit endpoints (max $2^4$ devices)
- SOF
	- Ensure timing of USB
	- No device responds
#### DATA
![[Pasted image 20240109042707.png]]
- Device must alternate between the two PIDs after each consecutive data packet 
- 8 bytes for Low speed
- 64 bytes for High speed
- After data, 16-bit CRC to ensure data correction.
##### PIDs
- DATA0
- DATA1


#### Handshake
![[Pasted image 20240109043230.png]]
##### PIDs
- ACK
- NACK
- STALL
	Outstanding error