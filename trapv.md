## TRAPV Trap on overflow

## Operation
IF V = 1 THEN:
[SSP] ← [SSP] - 4; [M([SSP])] ← [PC];
[SSP] ← [SSP] - 2; [M([SSP])] ← [SR];
[PC] ← [M($01C)]
ELSE no action
## Syntax
```assembly
TRAPV
```

## Attributes
Unsized

## Description
If the V-bit in the CCR is set, then initiate exception processing.
The exception vector is located at address 01C 16. This instruction
is used in arithmetic operations to call the operating system if
overflow occurs.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|-|-|-|-|
