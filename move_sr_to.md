## MOVE from SR Copy data from SR to

## destination

## Operation
[destination] ← [SR]

## Syntax
```assembly
MOVE SR,<ea>
```

## Attributes
Size = word

## Description
Move the contents of the status register to the destination location.
The source operand, the status register, is a word. This instruction
is not privileged in the 68000, but is privileged in the 68010, 68020,
and 68030. Executing a MOVE SR,<ea> while in the user mode on
these processors results in a privilege violation trap.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|-|-|-|-|

## Destination operand addressing modes
|Dn|An|(An)|(An)+|-(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||
