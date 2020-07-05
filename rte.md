## RTE Return from exception

## Operation
IF [S] = 1 THEN
[SR] ← [M([SP])]; [SP] ← [SP] + 2
[PC] ← [M([SP])]; [SP] ← [SP] + 4
ELSE TRAP


## Syntax
```assembly
RTE
```

## Attributes
Unsized

## Description
The status register and program counter are pulled from the stack.
The previous values of the SR and PC are lost. The RTE is used to
terminate an exception handler. Note that the behavior of the
RTE instruction depends on the nature of both the exception and
processor type. The 68010 and later models push more information on the stack following an exception than the 68000. The
processor determines how much to remove from the stack.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

The CCR is restored to its pre-exception state.

