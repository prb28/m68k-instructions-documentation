## SUB Subtract binary

## Operation
[destination] ← [destination] - [source]

## Syntax
SUB <ea>,Dn
SUB Dn,<ea>

## Attributes
Size = byte, word, longword

## Description
Subtract the source operand from the destination operand and
store the result in the destination location.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|*|*|*|*|*|

## Source operand addressing modes
|Dn|An|(An)|(An)+|-(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||


## Destination operand addressing modes
|Dn|An|(An)|(An)+|-(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||

