# NTSC-U
```
C25699AC 00000003
935C0074 399CFEAC
3D60UUUU 616BLLLL
916C0000 00000000
```
Recommended UUUU/LLLL Values
4250/0000: Low clip
4285/5000: Normal clip
4299/FFFF: Good clip
4300/0000: High clip
4350/0000: Higher clip
4375/0000: INSANE clip
I wouldn't recommend going higher than these since it may make you fly FOREVER.... but, im not in charge of you. So do what you plead :)
Going any lower doesnt yield very interesting results btw.
Negative values warp you to limbo lololol
# Assembly 1 (Runs at walltouch)
(DEFAULT INSTRUCTION) (RUNS WHEN TOUCHING WALL)
```
stw r26,0x0074(r28) 
```
```
subi r12,r28,0x154 (GET THE Y VELOCITY ADDRESS, put into r12)
lis r11,0xUUUU (Set upper 2 bytes to UUUU)
ori r11,r11,0xLLLL (Set lower 2 bytes to LLLL)
stw r11,0(r12) (Store the 4 bytes of r24 (VVVVYYYY) into Y velocity address!!!)
```
