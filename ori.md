## ORI OR immediate

## Operation
[destination] ← <literal> + [destination]

## Syntax
```assembly
ORI #<data>,<ea>
```

## Attributes
Size = byte, word, longword

## Description
OR the immediate data with the destination operand. Store the
result in the destination operand.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|*|*|0|0|

## Application
ORI forms the logical OR of the immediate source with the
effective address, which may be a memory location. For example,

```
ORI.B #%00000011,(A0)+
```

## Destination operand addressing modes
|Dn|An|(An)|(An)+|-(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||