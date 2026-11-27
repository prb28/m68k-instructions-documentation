# EORI - Exclusive-OR immediate

## Operation
[destination] ← \<literal\> ⊕ [destination]

## Syntax
```assembly
EORI #<data>,<ea>
```

## Attributes
`Size` byte, word, longword

## Description
EOR the immediate data with the contents of the destination operand. Store the result in the destination operand.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|*|*|0|0|

 - X: Not affected.
 - N: Set if the most significant bit of the result is set, cleared otherwise.
 - Z: Set if the result is zero, cleared otherwise.
 - V: Always cleared.
 - C: Always cleared.

## Destination operand addressing modes
|Dn|An|(An)|(An)+|&#x2011;(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||

# EORI to CCR - Exclusive-OR immediate to CCR

## Operation
[CCR] ← \<literal\> ⊕ [CCR]

## Syntax
```assembly
EORI #<data>,CCR
```
## Attributes
`Size` byte

## Description
EOR the immediate data with the contents of the condition code register (i.e., the least-significant byte of the status register).

## Application
Used to toggle bits in the CCR. For example, `EORI #$0C,CCR` toggles the N- and Z-bits of the CCR.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

 - X: changed if bit 4 of data = 1, unchanged otherwise.
 - N: changed if bit 3 of data = 1, unchanged otherwise.
 - Z: changed if bit 2 of data = 1, unchanged otherwise.
 - V: changed if bit 1 of data = 1, unchanged otherwise.
 - C: changed if bit 0 of data = 1, unchanged otherwise.

# EORI to SR - Exclusive-OR immediate to status register

## Operation
IF [S] = 1<br/>
&nbsp;THEN<br/>
&nbsp;&nbsp;[SR] ← \<literal\> ⊕ [SR]<br/>
&nbsp;ELSE TRAP<br/>

## Syntax
```assembly
EORI #<data>,SR
```
## Attributes
`Size` word

## Description
EOR (exclusive OR) the immediate data with the contents of the status register and store the result in the status register. All bits of the status register are affected.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

 - X: changed if bit 4 of data = 1, unchanged otherwise.
 - N: changed if bit 3 of data = 1, unchanged otherwise.
 - Z: changed if bit 2 of data = 1, unchanged otherwise.
 - V: changed if bit 1 of data = 1, unchanged otherwise.
 - C: changed if bit 0 of data = 1, unchanged otherwise.

*From MOTOROLA M68000 FAMILY Programmer's reference manual. Copyright 1992 by Motorola Inc./NXP. Adapted with permission.*