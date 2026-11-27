# NBCD - Negate decimal with sign extend

## Operation
[destination]<sub>10</sub> ← 0 − [destination]<sub>10</sub> - [X]

## Syntax
```assembly
NBCD <ea>
```

## Attributes
`Size`  byte

## Description
The operand addressed as the destination and the extend bit in the CCR are subtracted from zero. The subtraction is performed using binary coded decimal (BCD) arithmetic. This instruction calculates the ten's complement of the destination if the X-bit is clear, and the nine's complement if X = 1. This is a byte-only operation. Negating a BCD number (with X = 0) has the effect of subtracting it from 100<sub>10</sub>.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|U|*|U|*|

 - X: Set the same as the carry bit.
 - N: Undefined.
 - Z: Cleared if the result is nonzero, unchanged otherwise.
 - V: Undefined.
 - C: Set if a decimal borrow occurs, cleared otherwise.

The C-bit is set if a decimal borrow occurs.

## Destination operand addressing modes
|Dn|An|(An)|(An)+|&#x2011;(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||

*From MOTOROLA M68000 FAMILY Programmer's reference manual. Copyright 1992 by Motorola Inc./NXP. Adapted with permission.*