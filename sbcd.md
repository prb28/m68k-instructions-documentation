## SBCD Subtract decimal with extend

## Operation
[destination] 10 ← [destination] 10 - [source] 10 - [X]

## Syntax
SBCD Dy,Dx
SBCD -(Ay),-(Ax)

## Attributes
Size = byte

## Description
Subtract the source operand from the destination operand together
with the X-bit, and store the result in the destination. Subtraction
is performed using BCD arithmetic. The only legal addressing
modes are data register direct and memory to memory with
address register indirect using auto-decrementing.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|U|*|U|*|

Z: Cleared if result is non-zero. Unchanged otherwise. The Z-bit
can be used to test for zero after a chain of multiple precision
operations.

