## Cyclic redundancy check

- More powerful error-detection coding 
- View data bits, D, as a binary number 
- Choose r +1 bit pattern (generator), G 
- Goal: choose r CRC bits, R, such that 
	- exactly divisible by G (modulo 2) 
	- receiver knows G, <D, R> divides by G. If non-zero remainder: error detected! 
	- can detect all burst errors less than r +1 bits 
- Widely used in practice (Ethernet, 802.11 WiFi, ATM)

==D== - Data blocks
==G== - Divisor
==CRC== - remainder
![[Pasted image 20230330152610.png]]
Task:
Find the CRC for the data blocks 100100 with the divisor 1101
1) Append to (divizer length - 1) zeros to D (yellow 000)
2) Perform Binary Division
3) CRC - remainder
4) Data Transmitted - Appending CRC to D
![[Pasted image 20230330155054.png]]
