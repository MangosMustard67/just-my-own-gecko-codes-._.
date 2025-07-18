# NTSC-U
```
C25699AC 00000003
935C0074 399CFEAC
3F00VVVV 6318YYYY
930C0000 00000000
```
Recommended VVVV/YYYY values:
VVVV/YYYY: 4F4F/BFBF , Highclip
# (Assembly)
(DEFAULT INSTRUCTION) (RUNS WHEN TOUCHING KCL FLAG 0XC (WALL))
```
stw r26,0x0074(r28) 
```
```
subi r12,r28,0x154 (GET THE Y VELOCITY ADDRESS)
lis r24,0xVVVV   (Set upper 2 bytes to VVVV)
ori r24,r24,0xYYYY (Set lower 2 bytes to YYYY)
stw r24,0(r12) (Store the 4 bytes into Y velocity address
```
too mught heiight is fall
lhz r11, 0x0078 (r3)
cmpwi r11,0x4000
ble 0xC
lis r12, 0xFFFF
stw r12, 0x0078 (r3)
stfs f1, 0x0078 (r3)
