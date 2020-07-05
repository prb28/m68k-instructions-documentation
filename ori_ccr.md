## ORI to CCR Inclusive OR immediate to CCR

## Operation
[CCR] ← <literal> + [CCR]

## Syntax
```assembly
ORI #<data>,CCR
```

## Attributes
Size = byte

## Description
OR the immediate data with the condition code register (i.e., the
least-significant byte of the status register). For example, the Z
flag of the CCR can be set by ORI #$04,CCR.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

X is set if bit 4 of data = 1; unchanged otherwise
N is set if bit 3 of data = 1; unchanged otherwise
Z is set if bit 2 of data = 1; unchanged otherwise
V is set if bit 1 of data = 1; unchanged otherwise
C is set if bit 0 of data = 1; unchanged otherwise