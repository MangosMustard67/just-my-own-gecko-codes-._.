# NTSC-U

C25201C8 0000001F
B0050000 8981E3F0
39600001 2C001000
418200D8 2C000200
418200A8 2C000100
418200B4 2C000008
41820020 2C000004
4182002C 2C000002
41820060 2C000001
41820030 480000B0
2C0C0002 418100A8
7D8B6214 9981E3F0
4800009C 2C0C0004
41810094 7D8B6214
9981E3F0 48000088
2C0C0005 41810010
7D8B6214 9981E3F0
48000074 2C0C0007
4082006C 7D8B6214
9981E3F0 48000060
2C0C0006 41810010
7D8B6214 9981E3F0
4800004C 2C0C0008
40820044 7D8B6214
9981E3F0 48000038
2C0C0009 40820030
7D8B6214 9981E3F0
48000024 2C0C000A
4082001C 7D8B6214
9981E3F0 48000010
2C0C000B 40820008
B841E3F0 00000000

# NTSC-J

C2523FBC 0000001F
B0050000 8981E3F0
39600001 2C001000
418200D8 2C000200
418200A8 2C000100
418200B4 2C000008
41820020 2C000004
4182002C 2C000002
41820060 2C000001
41820030 480000B0
2C0C0002 418100A8
7D8B6214 9981E3F0
4800009C 2C0C0004
41810094 7D8B6214
9981E3F0 48000088
2C0C0005 41810010
7D8B6214 9981E3F0
48000074 2C0C0007
4082006C 7D8B6214
9981E3F0 48000060
2C0C0006 41810010
7D8B6214 9981E3F0
4800004C 2C0C0008
40820044 7D8B6214
9981E3F0 48000038
2C0C0009 40820030
7D8B6214 9981E3F0
48000024 2C0C000A
4082001C 7D8B6214
9981E3F0 48000010
2C0C000B 40820008
B841E3F0 00000000

# NTSC-K

C2512660 0000001F
B0050000 8981E3F0
39600001 2C001000
418200D8 2C000200
418200A8 2C000100
418200B4 2C000008
41820020 2C000004
4182002C 2C000002
41820060 2C000001
41820030 480000B0
2C0C0002 418100A8
7D8B6214 9981E3F0
4800009C 2C0C0004
41810094 7D8B6214
9981E3F0 48000088
2C0C0005 41810010
7D8B6214 9981E3F0
48000074 2C0C0007
4082006C 7D8B6214
9981E3F0 48000060
2C0C0006 41810010
7D8B6214 9981E3F0
4800004C 2C0C0008
40820044 7D8B6214
9981E3F0 48000038
2C0C0009 40820030
7D8B6214 9981E3F0
48000024 2C0C000A
4082001C 7D8B6214
9981E3F0 48000010
2C0C000B 40820008
B841E3F0 00000000

# PAL

C252463C 0000001F
B0050000 8981E3F0
39600001 2C001000
418200D8 2C000200
418200A8 2C000100
418200B4 2C000008
41820020 2C000004
4182002C 2C000002
41820060 2C000001
41820030 480000B0
2C0C0002 418100A8
7D8B6214 9981E3F0
4800009C 2C0C0004
41810094 7D8B6214
9981E3F0 48000088
2C0C0005 41810010
7D8B6214 9981E3F0
48000074 2C0C0007
4082006C 7D8B6214
9981E3F0 48000060
2C0C0006 41810010
7D8B6214 9981E3F0
4800004C 2C0C0008
40820044 7D8B6214
9981E3F0 48000038
2C0C0009 40820030
7D8B6214 9981E3F0
48000024 2C0C000A
4082001C 7D8B6214
9981E3F0 48000010
2C0C000B 40820008
B841E3F0 00000000


# ASM SOURCE CODE
Insert address pattern is USA/JAP/KOR/PAL
```
C25201C8/C2523FBC/C2512660/C252463C
sth r0, 0x0 (R5)
lbz r12, -0x1C10(sp)
li r11, 0x1

cmpwi r0, 0x1000
beq start_code
cmpwi r0, 0x0200
beq b_code
cmpwi r0, 0x0100
beq a_code
cmpwi r0, 0x8
beq up_code
cmpwi r0, 0x4
beq down_code
cmpwi r0, 0x2
beq right_code
cmpwi r0, 0x1
beq left_code
b end

up_code:
cmpwi r12, 0x2
bgt end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

down_code:
cmpwi r12, 0x4
bgt end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

left_code:
cmpwi r12, 0x5
bgt check_left
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

check_left:
cmpwi r12, 0x7
bne end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

right_code:
cmpwi r12, 0x6
bgt check_right
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

check_right:
cmpwi r12, 0x8
bne end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

b_code:
cmpwi r12, 0x9
bne end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

a_code:
cmpwi r12, 0xA
bne end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

start_code:
cmpwi r12, 0xB 
bne end
lmw r2, -0x1C10(sp)
end:
```
# ASM SOURCE CODE (WITH COMMENTS)
```
C25201C8/C2523FBC/C2512660/C252463C
sth r0, 0x0 (R5) (Default instruction that stores our current button pressed into r5's address)
lbz r12, -0x1C10(sp) (r12 is our Konami Code status)
li r11, 0x1 (r11 is zero)

cmpwi r0, 0x1000 (Check if we're pressing start button and branch to start code if so)
beq start_code
cmpwi r0, 0x0200 (Check if we're pressing b button and branch to b code if so)
beq b_code 
cmpwi r0, 0x0100 (You get the idea.)
beq a_code
cmpwi r0, 0x8
beq up_code
cmpwi r0, 0x4
beq down_code
cmpwi r0, 0x2
beq right_code
cmpwi r0, 0x1
beq left_code
b end (If its none of these then just end the code.)

up_code:
cmpwi r12, 0x2
bgt end (If we've already pressed up twice then this code stops.)
add r12, r11, r12 (Add 1 to our current konami status.) 
stb r12, -0x1C10(sp) (Store our new Konami Status.)
b end

down_code:
cmpwi r12, 0x4 (If we've already press down twice then stop the code)
bgt end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

left_code:
cmpwi r12, 0x5
bgt check_left (If we've already pressed left then see if we're doing it for the second left press.)
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

check_left:
cmpwi r12, 0x7 (See if we're currently on the second left press)
bne end (If not then end the code, otherwise add 1 to our Konami Status and store it.)
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

right_code:
cmpwi r12, 0x6 (Same as left code, if we've already pressed right then see if we're doing it for the second time.)
bgt check_right
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

check_right:
cmpwi r12, 0x8 (See if we're on second right press.)
bne end (If not then end code.)
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

b_code:
cmpwi r12, 0x9 (See if we're on the B press)
bne end (End code if not, otherwise update Konami Status.)
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

a_code:
cmpwi r12, 0xA (See if we're on the A press.)
bne end
add r12, r11, r12
stb r12, -0x1C10(sp)
b end

start_code:
cmpwi r12, 0xB (See if we're on the start press)
bne end (Otherwise, end the code)
lmw r2, -0x1C10(sp) (THIS is where the magic happens. The game code after this will try to read from invalid memory (0x00000000), Causing panic handlers on Dolphin & a nice sound for Dolphin AND wii! :3)

end:
```
