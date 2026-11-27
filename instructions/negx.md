# NEGX - Negate with extend

## Operation
[destination] ← 0 - [destination] - [X]

## Syntax
```assembly
NEGX <ea>
```

## Attributes
`Size`  byte, word, longword

## Description
The operand addressed as the destination and the extend bit are subtracted from zero. `NEGX` is the same as `NEG` except that the X-bit is also subtracted from zero.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

 - X: Set the same as the carry bit.
 - N: Set if the result is negative, cleared otherwise.
 - Z: Cleared if the result is nonzero, unchanged otherwise.
 - V: Set if an overflow occurs, cleared otherwise.
 - C: Set if a borrow occurs, cleared otherwise.

## Destination operand addressing modes
|Dn|An|(An)|(An)+|&#x2011;(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||

*From MOTOROLA M68000 FAMILY Programmer's reference manual. Copyright 1992 by Motorola Inc./NXP. Adapted with permission.*