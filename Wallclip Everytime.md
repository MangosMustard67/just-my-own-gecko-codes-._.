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
stw r11,0(r12) (Store the 4 bytes of r11 (UUUULLLL) into Y velocity address!!!)
```
Button activated MKWII  (GCN CONTROLLER)
UUUU/LLLL VALUES = Wallclip Height
ZZZZ/zzzz VALUES = Enable and Disable code.
```
C25699AC 00000006
935C0074 3D808000
618C3B00 816C0000
280B0001 40820014
399CFEAC 3D60UUUU
616BLLLL 916C0000
60000000 00000000
C251D060 00000008
B01E005E 3D808000
618C3B00 A16C0000
2C00ZZZZ 40820010
39600001 916C0000
48000014 2C00zzzz
4082000C 39600000
916C0000 60000000
60000000 00000000

```
Write up
```
sth r0, 0x005e(r30) (default instruction)
lis r12, 0x8000
ori r12,r12, 0x3B00
lhz r11, 0x0 (r12)
cmpwi r0, 0x1000
bne check
li r11, 0x1
stw r11, 0x0(r12)
b end
check: 
cmpwi r0, 0x1100
bne end
li r11, 0x0
stw r11, 0x0(r12)
end:
```
