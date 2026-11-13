1. M=34 ejecutar:
	- M<<1
	- M>>2
	- M>>1
	- Encender 3 bit

M a bitmask = 00100010
M<<1: 01000100 = 68
M>>2: 00001000 = 8
M>>1: 00010001 = 17
M | (1<<3): 00101010 = 42

2. M=42 ejecutar:
	- Check bit 3
	- Check bit 2
	- Apagar bit 1

M a bitmask = 0101010
M & (1<<3): 1
M & (1<<2): 0
M & ~(1<<1): 0101000

3. M=
