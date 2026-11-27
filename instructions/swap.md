# SWAP - Swap register halves

## Operation
[Register(16:31)] ← [Register(0:15)];<br/>
[Register(0:15)] ← [Register(16:31]

## Syntax
```assembly
SWAP Dn
```

## Attributes
`Size` word

## Description
Exchange the upper and lower 16-bit words of a data register.

## Application
The `SWAP Dn` instruction enables the higher-order word in a register to take part in word operations by moving it into the lower-order position. `SWAP Dn` is effectively equivalent to `ROR.L Di,Dn`, where [Di] = 16. However, `SWAP` clears the C-bit of the *CCR*, whereas `ROR` sets it according to the last bit to be shifted into the carry bit.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|*|*|0|0|

 - X: Not affected.
 - N: Set if the most significant bit of the 32-bit result is set, cleared otherwise.
 - Z: Set if the 32-bit result is zero, cleared otherwise.
 - V: Always cleared.
 - C: Always cleared.

*From MOTOROLA M68000 FAMILY Programmer's reference manual. Copyright 1992 by Motorola Inc./NXP. Adapted with permission.*