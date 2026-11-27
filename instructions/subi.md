# SUBI - Subtract immediate

## Operation
[destination] ← [destination] - \<literal\>

## Syntax
```assembly
SUBI #<data>,<ea>
```

## Attributes
`Size` byte, word, longword

## Description
Subtract the immediate data from the destination operand. Store the result in the destination operand.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

 - X: Set to the value of the carry bit.
 - N: Set if the result is negative, cleared otherwise.
 - Z: Set if the result is zero, cleared otherwise.
 - V: Set if an overflow occurs, cleared otherwise.
 - C: Set if a borrow occurs, cleared otherwise.

## Destination operand addressing modes
|Dn|An|(An)|(An)+|&#x2011;(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||

*From MOTOROLA M68000 FAMILY Programmer's reference manual. Copyright 1992 by Motorola Inc./NXP. Adapted with permission.*