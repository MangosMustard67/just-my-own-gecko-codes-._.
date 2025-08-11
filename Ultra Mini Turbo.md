# Ultra Mini Turbo

Name is self explanatory. This is my best code and im so very proud of it :)
It is almost 1:1 with the Retro Rewind ultra mini turbos, that's how polished it is.
Credits to maritoguionyo (https://mariokartwii.com/member.php?action=profile&uid=421) for telling me how to optimize this code, helping me improve my ASM a LOT, and most importantly, telling me how to port codes. I can not thank him enough honestly.

# NTSC-U
```
C25AA544 00000014
399EEBEC A16C0000
2C0B0003 40820078
886C0159 2C030010
4182007C A16C005C
280BBF80 4182002C
280B3F80 41820024
48000004 39600002
A00C0016 7D6B0214
2C0B014A B16C0016
40800024 48000048
39600005 A00C0016
7D6B0214 2C0B014A
B16C0016 40800008
4800002C 3960014A
B16C0016 38600002
B06C0004 B06C0000
48000014 A16C0016
2C0B014A 40820008
4BFFFFDC 807E0078
60000000 00000000
C257C89C 00000004
A17D0112 2C0B014A
4182000C B3FD010C
4800000C 1FFF0008
B3FD010C 00000000
C257C8A8 00000005
2C0B014A 40820018
38000004 B01D0118
A19D010C B19D0110
48000008 B01D0118
60000000 00000000
C2577768 00000002
B09D00FC B09D0112
60000000 00000000
```
# NTSC-J
```
C25B4DEC 00000014
399EEBEC A16C0000
2C0B0003 40820078
886C0159 2C030010
4182007C A16C005C
280BBF80 4182002C
280B3F80 41820024
48000004 39600002
A00C0016 7D6B0214
2C0B014A B16C0016
40800024 48000048
39600005 A00C0016
7D6B0214 2C0B014A
B16C0016 40800008
4800002C 3960014A
B16C0016 38600002
B06C0004 B06C0000
48000014 A16C0016
2C0B014A 40820008
4BFFFFDC 807E0078
60000000 00000000
C2582A80 00000004
A17D0112 2C0B014A
4182000C B3FD010C
4800000C 1FFF0008
B3FD010C 00000000
C2582A8C 00000005
2C0B014A 40820018
38000004 B01D0118
A19D010C B19D0110
48000008 B01D0118
60000000 00000000
C257D94C 00000002
B09D00FC B09D0112
60000000 00000000
```
# NTSC-K
```
C25A34C4 00000014
399EEBEC A16C0000
2C0B0003 40820078
886C0159 2C030010
4182007C A16C005C
280BBF80 4182002C
280B3F80 41820024
48000004 39600002
A00C0016 7D6B0214
2C0B014A B16C0016
40800024 48000048
39600005 A00C0016
7D6B0214 2C0B014A
B16C0016 40800008
4800002C 3960014A
B16C0016 38600002
B06C0004 B06C0000
48000014 A16C0016
2C0B014A 40820008
4BFFFFDC 807E0078
60000000 00000000
C2571158 00000004
A17D0112 2C0B014A
4182000C B3FD010C
4800000C 1FFF0008
B3FD010C 00000000
C2571164 00000005
2C0B014A 40820018
38000004 B01D0118
A19D010C B19D0110
48000008 B01D0118
60000000 00000000
C256C024 00000002
B09D00FC B09D0112
60000000 00000000
```
# PAL
```
C25B546C 00000014
399EEBEC A16C0000
2C0B0003 40820078
886C0159 2C030010
4182007C A16C005C
280BBF80 4182002C
280B3F80 41820024
48000004 39600002
A00C0016 7D6B0214
2C0B014A B16C0016
40800024 48000048
39600005 A00C0016
7D6B0214 2C0B014A
B16C0016 40800008
4800002C 3960014A
B16C0016 38600002
B06C0004 B06C0000
48000014 A16C0016
2C0B014A 40820008
4BFFFFDC 807E0078
60000000 00000000
C2583100 00000004
A17D0112 2C0B014A
4182000C B3FD010C
4800000C 1FFF0008
B3FD010C 00000000
C258310C 00000005
2C0B014A 40820018
38000004 B01D0118
A19D010C B19D0110
48000008 B01D0118
60000000 00000000
C257DFCC 00000002
B09D00FC B09D0112
60000000 00000000
```
#******ASM SOURCE CODE******

# INSERT ADDRESSES PATTERN IS NTSC-U/JAP/KOR/PAL
```
C25AA544/C25B4DEC/C25A34C4/C25B546C

subi r12, r30, 0x1414
lhz r11, 0x0 (R12)
cmpwi r11, 0x3
bne check

checkthewiggle:
lbz r3, 0x159(r12)
cmpwi r3, 0x10
beq end
lhz r11, 0x5C(r12)
cmplwi r11, 0xBF80
beq changeby5
cmplwi r11, 0x3F80
beq changeby5
b changeby2

changeby2:
li r11, 0x2
lhz r0, 0x16(r12)
add r11, r11, r0
cmpwi r11, 0x14A
sth r11, 0x16(r12)
bge changetheMT
b end

changeby5:
li r11, 0x5
lhz r0, 0x16(r12)
add r11, r11, r0
cmpwi r11, 0x14A
sth r11, 0x16(r12)
bge changetheMT
b end

changetheMT:
li r11, 0x14A
sth r11, 0x16(r12)             
li r3, 0x2
sth r3, 0x4 (r12) 
sth r3, 0x0(r12)
b end

check:
lhz r11, 0x16 (r12)
cmpwi r11, 0x14A
bne end
b changetheMT
end:
lwz	r3, 0x0078 (r30)

C257C89C/C2582A80/C2571158/C2583100

lhz r11,0x112(r29)
cmpwi r11,0x14A
beq ULTRA
sth r31,0x10C(r29)
b end
ULTRA:
mulli r31,r31,8
sth r31,0x10C(r29)
end:

C257C8A8/C2582A8C/C2571164/C258310C

cmpwi r11,0x14A
bne- default
alter:
li r0,4
sth r0,0x118(r29)
lhz r12, 0x010C(r29)
sth r12, 0x110(r29)
b end
default:
sth r0,0x118(r29)
end:

C2577768/C257D94C/C256C024/C257DFCC

sth r4, 0x00FC(r29)
sth r4, 0x0112(r29)
```

# *** SOURCE WITH COMMENTS***

```
C25AA544/C25B4DEC/C25A34C4/C25B546C (Main code)

subi r12, r30, 0x1414 (r12 is Driftstatus address)
lhz r11, 0x0 (R12) (r11 is Driftstatus value)
cmpwi r11, 0x3 (Check if we have orange mini turbo)
bne check

checkthewiggle:  (Check how tight we are drifting)
lbz r3, 0x159(r12) (Put a value that changes if we're in the air in r3)
cmpwi r3, 0x10 (See if we're in the air)
beq end (End code if so)
lhz r11, 0x5C(r12) (Put our drift intensity into r11)
cmplwi r11, 0xBF80 (Compare it to maximum right drift intensity)
beq changeby5 (If its equal then change our UMT halfword by 5)
cmplwi r11, 0x3F80 (Compare it to maximum left drift intensity)
beq changeby5 (Change UMT halfword by 5 if equal)
b changeby2 (Otherwise just change our UMT halfword by 2.)

changeby2:  (Change our UMT halfword by 2)
li r11, 0x2 (r11 is 2)
lhz r0, 0x16(r12) (r0 is UMT halfword value)
add r11, r11, r0 (add 2 to our UMT halfword value)
cmpwi r11, 0x14A (See if we reached the UMT threshold)
sth r11, 0x16(r12) (Store our new UMT halfword value)
bge changetheMT (Give us a blue mini turbo if greater than or equal to max threshold)
b end

changeby5: (Change our UMT halfword by 5)
li r11, 0x5 
lhz r0, 0x16(r12)
add r11, r11, r0
cmpwi r11, 0x14A
sth r11, 0x16(r12)
bge changetheMT
b end

changetheMT: (Make our mini turbo blue)
li r11, 0x14A (make r11 our UMT threshold)
sth r11, 0x16(r12) (Store it into our UMT value (incase our value is greater than 0x14A.))
li r3, 0x2 (r3 is 2)
sth r3, 0x4 (r12) (Make our orange mini turbo value 2(not 0 for the sake of code space))
sth r3, 0x0(r12) (Make our driftstatus 2, giving us a BLUUUUUUUUUE mini turbo OwO >w< 😛😛😛(with max UMT duh.))
b end 

check: (Check if we have max UMT value and make our mini turbo blue if so.)
lhz r11, 0x16 (r12) (Load our UMT halfword into r11)
cmpwi r11, 0x14A (compare r11 to max UMT value)
bne end
b changetheMT 
end:
lwz	r3, 0x0078 (r30) (Default instruction. This and the code afterward load values into r3 and r0, meaning our code uses 100% safe registers :]. No game crashes here!)

C257C89C/C2582A80/C2571158/C2583100 (Give us extra boost when we release blue mini turbo with max UMT threshold)

lhz r11,0x112(r29) (Put UMT Halfword in r11)
cmpwi r11,0x14A (Compare it to the threshold)
beq ULTRA (Multiply our boost if equal)
sth r31,0x10C(r29) (Default instruction that puts our boost halfword in r29 + 0x10C)
b end
ULTRA: (Multiply our boost and then do default instruction)
mulli r31,r31,0x8  (r31 = r31 x 8)
sth r31,0x10C(r29) (Default instruction)
end:

C257C8A8/C2582A8C/C2571164/C258310C (Give us more speed when we release our ultra mini turbo)

cmpwi r11,0x14A ( R11 is still the UMT halfword because this code runs a bit after C257C89C. )
bne- default (Do the default instruction if not equal)
alter: (Give us a mushroom speed boost) 
li r0,4 (4 is the mushroom boost value)
sth r0,0x118(r29) (Change our players boost value to mushrooming)
lhz r12, 0x010C(r29) (Load our mini turbo boost amount from the previous function)
sth r12, 0x110(r29) (Store it in our mushroom boost halfword)
b end
default:
sth r0,0x118(r29) (Default instruction)
end:

C2577768/C257D94C/C256C024/C257DFCC (Zero our UMT halfword whenever we do something that gets rid of our mini turbo)

sth r4, 0x00FC(r29) (Default instruction that changes our driftstatus to 0)
sth r4, 0x0112(r29) (Set our UMT value to 0.)
```
