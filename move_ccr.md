## MOVE to CCR Copy data to CCR from source

## Operation
[CCR] ← [source]

## Syntax
```assembly
MOVE <ea>,CCR
```

## Attributes
Size = word

## Description
Move the contents of the source operand to the condition code
register. The source operand is a word, but only the low-order
byte contains the condition codes. The upper byte is neglected.
Note that MOVE <ea>,CCR is a word operation, but ANDI, ORI, and
EORI to CCR are all byte operations.

## Application
The move to CCR instruction permits the programmer to preset
the CCR. For example, MOVE #0,CCR clears all the CCRís bits.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

## Source operand addressing modes
|Dn|An|(An)|(An)+|-(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||
