## MOVE USP Copy data to or from USP

Operation 1: IF [S] = 1 {MOVE USP,An form}
THEN [USP] ← [An]
ELSE TRAP

Operation 2: IF [S] = 1 {MOVE An,USP form}
THEN [An] ← [USP]
ELSE TRAP

Syntax 1: MOVE USP,An
Syntax 2: MOVE An,USP

## Attributes
Size = longword

## Description
Move the contents of the user stack pointer to an address register
or vice versa. This is a privileged instruction and allows the
operating system running in the supervisor state either to read
the contents of the user stack pointer or to set up the user stack
pointer.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|-|-|-|-|