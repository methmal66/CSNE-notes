---
tag: electronic programming ES
aliases: Opt codes
---

https://www.cs.virginia.edu/~evans/cs216/guides/x86.html

> Instructions in [[Assembly]], aka opt codes

# What are the common mnemonics used in [[AVR]]s?
## Immediate instructions
###### `ldi`
Load a value to a register. Can use with only R16-R31

Assign a decimal value
```asm
ldi  r16,  65         ;r16  = 65 (decimal)
```

Assign a binary value
```asm
ldi r20,  0b110101    ;r20 = 00110101 (binary)
```

Assign a hexa decimal value
```asm
ldi  r23, 0xcf        ;r23 = 0xcf (hexa)
```

## Arithmatic operators
###### `add`
Add a two values and save the total in the first register

34 + 10
```asm
ldi r16, 19    ;r16 = 19
ldi r17, 95    ;r17 = 95
add r16, r17   ;r16 = r16 + r17
```

120 + 23
```asm
ldi r30, 120   ;r30 = 120
ldi r30, 23    ;r30 = r30 + 23
```

5 + 10 + 15
```asm
ldi r20, 5     ;r20 = 5
ldi r21, 10    ;r21 = 10
add r20, r21   ;r20 = r20 + r21
ldi r21, 15    ;r21 = 15
add r20, r21   ;r20 = r20 + r21
```

###### `sub`
Subtract a two values and save the total in the first register

100 - 20
```asm
ldi r18, 100   ;r18 = 100
sub r18, 20    ;r18 = r18 - 20
```

50 - 13
```asm
ldi r20, 50    ;r20 = 50
ldi r21, 13    ;r21 = 13
sub r20, r21   ;r20 = r20 - r21
```

60 - 30 - 15
```asm
ldi r20, 60    ;r20 = 60
ldi r21, 30    ;r21 = 30
sub r20, r21   ;r20 = r20 - r21
ldi r21, 15    ;r21 = 15
sub r20, r21   ;r20 = r20 - r21
```

###### `inc`
Increment the value of a register by one

100 + 1
```asm
ldi r20, 100  ;r20 = 100
inc r20       ;r20 = r20 + 1
```

###### `dec`
Decrement the value of a register by one

100 - 1
```asm
ldi r20, 100  ;r20 = 100
dec r20       ;r20 = r20 - 1
```



###### `mul`
Multiply two values and save the total in the first register

10 * 5
```asm 
ldi r20, 10    ;r20 = 10
mul r20, 5     ;r20 = r20 * 5
```
 
###### `div`

## Bitwise operators
###### `and`
Perfome logical AND to the second value and save the output in the first register

0x8a AND 0xff
```asm
ldi r20, 0x8a   ;r20 = 0x8a
and r20, 0xff   ;r20 = r20 and 0xff
```

###### `or`
Perfome logical OR to the second value and save the output in the first register

0x8a OR 0xff
```asm
ldi r20, 0x8a   ;r20 = 0x8a
or r20, 0xff   ;r20 = r20 or 0xff
```

###### `xor`
Perfome logical XOR to the second value and save the output in the first register

0x8a XOR 0xff
```asm
ldi r20, 0x8a   ;r20 = 0x8a
xor r20, 0xff   ;r20 = r20 xor 0xff
```

###### `not`
Flit all the bit values

(11010101)'
```asm
ldi r20, 0b11010101
not r20
```

###### `shl`
shift the bits in their first operand's contents left and padding the resulting empty bit positions with zeros. The output is saved tin the first operand. The number of bits to shift is specified by the second operand.

0001000
```asm
ldi r20, 1   ;r20 = 1
shl r20, 3   ;r20 = r20 <<< 3
```

###### `shr`
shift the bits in their first operand's contents right and padding the resulting empty bit positions with zeros. The output is saved tin the first operand. The number of bits to shift is specified by the second operand.

00001000
```asm
ldi r20, 127   ;r20 = 127
shr r20, 4   ;r20 = r20 >>> 4
```

## Other operators
###### `clr`
###### `out`
## Memory operators
###### `sts`
Store 55 into location 0x80 of RAM
```asm
ldi r16, 55
sts 0x80, r16
```

###### `lds`
Copy the contents of location 0x80 of RAM into location 0x81
```asm
lds r20, 0x80
sts 0x81, r20
```

Add contents at 0x90to contents at 0x95 and store the result in 0x313
```asm
lds r20, 0x90
lds r21, 0x95
add r20, r21
sts 0x313, r20
```

Store 0x53 into the SPH register at 0x5e
```asm
lds r20, 0x53
sts 0x53, r20
```

## I/O operations
###### `in`
Add the contents of the PINC I/O reg to the contents of PIND and stores the result in location 0x90 of the SRAM
```asm
in r20, pinc
in r21, pind
add r20, r21
sts 0x90, r20
```

###### `out`


## Flow control
### `rjmp`
Relative jump.
>[!important]- This is the most widely used jump

```assembly
ldi r16, 
```

>[!faq]- How to calculate the range of a jump
> Jump bits = 16 - 4 = 12
> Number of lines can be jumped = 2^12 = 4096

### `jmp`
>[!faq]- How to provide the jump address?
>- 

### `ijmp`

### `BRNE`
>[!faq]- What are the flags in SREG?
>

### `BRCC`

### `BRCS`

```assembly
sub r24, r26
brcc L1
inc r22
L1: 
```

>[!example]-
>```assembly
>```

### `PUSH`

### `POP`

### `CALL`


###### How to handle negative values in registers?

###### Why there are two addresses (memory and I/O)

