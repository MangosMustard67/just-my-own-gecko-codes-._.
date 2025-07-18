# NTSC-U
```
C25699AC 00000003
935C0074 281A000C
40820008 399CFEAC
1D8C0FFF 00000000


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
