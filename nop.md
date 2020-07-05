## NOP No operation

## Operation
None

## Syntax
```assembly
NOP
```

## Attributes
Unsized

## Description
The no operation instruction, NOP performs no computation.
Execution continues with the instruction following the NOP
instruction. The processor's state is not modified by a NOP.


## Application
NOPs can be used to introduce a delay in code. Some programmers
use them to provide space for patches ó two or more NOPs can
later be replaced by branch or jump instructions to fix a bug. This
use of the NOP is seriously frowned upon, as errors should be
corrected by re-assembling the code rather than by patching it.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|-|-|-|-|

