# NTSC-U
```
C25699AC 00000003
935C0074 399CFEAC
3F00VVVV 6318YYYY
930C0000 00000000
```
Recommended VVVV/YYYY values:
VVVV/YYYY: 4F4F/BFBF , Highclip
# Assembly 1 (Runs at walltouch)
(DEFAULT INSTRUCTION) (RUNS WHEN TOUCHING KCL FLAG 0XC (WALL))
```
stw r26,0x0074(r28) 
```
```
subi r12,r28,0x154 (GET THE Y VELOCITY ADDRESS, put into r12)
lis r24,0xVVVV   (Set upper 2 bytes to VVVV)
ori r24,r24,0xYYYY (Set lower 2 bytes to YYYY)
stw r24,0(r12) (Store the 4 bytes of r24 (VVVVYYYY) into Y velocity address!!!)
```
too mught heiight is fall (Address is responsible for your y velocity)
```
C25AA364 00000005
A1830078 81630240
2C0C4000 41800014
2C0B000C 4182000C
39600002 7D8C5BD6
D0230078 00000000
```
```
lhz r12, 0x0078 (r3) (Load Y velocity into r12)
lwz r11, 0x0240 (r3) (Load "wall is hit" flag into r11)
cmpwi r12, 0xMMMM (Check if Y velocity is greater than MMMM)
blt 0x14 (If velocity less than MMMM, branch to default instruction. Otherwise, keep going.)
cmpwi r11, 0xC (Check if touching wall)
beq 0xC (If touching wall, then stop. Otherwise, keep going bro.)
li r11, 0x2 (Set r11 to 0x2)
divw r12, r12, r11 (Divide my Y velocity by 2)
stfs f1, 0x0078 (r3) (DEFAULT INSTRUCTION)
```
