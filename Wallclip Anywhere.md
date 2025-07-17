# NTSC-U
```
C25699AC 00000004
935C0074 819C0074
280C000C 40820004
3D801FFF 819CFEAC
60000000 00000000
```
```
stw r26,0x0074(r28)
lwz r12,0x0074(r28)
cmplwi r12,12
bne- 0x04
lis r12,0x1fff
lwz r12,-154(r28)
nop
```
# (Assembly)
(DEFAULT INSTRUCTION)
```
stw r26,0x0074(r28) 
```
```
lhz r12,0x0074(r28)
cmplwi r12,0xc
bne 0x4
lis r12, 0x8004
ori r12, r12, 0x09b8
mtctr r12
bctr 
lis r26, 0x1FFF
lfd f1, 0x0(r26)
stfs f1, 0x0078(r3)
```
