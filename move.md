## MOVE Copy data from source to destination

## Operation
[destination] ← [source]

## Syntax
```assembly
MOVE <ea>,<e>
```

## Sample syntax
```assembly
MOVE (A5),-(A2)
MOVE -(A5),(A2)+
MOVE #$123,(A6)+
MOVE Temp1,Temp2
```


## Attributes
Size = byte, word, longword

## Description
Move the contents of the source to the destination location. The
data is examined as it is moved and the condition codes set
accordingly. Note that this is actually a copy command because
the source is not affected by the move. The move instruction has
the widest range of addressing modes of all the 68000ís
instructions.

## Condition codes
|X|N|Z|V|C|
|--|--|--|--|--|
|-|*|*|0|0|

## Source operand addressing modes
|Dn|An|(An)|(An)+|-(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||

## Destination operand addressing modes
|Dn|An|(An)|(An)+|-(An)|(d,An)|(d,An,Xi)|ABS.W|ABS.L|(d,PC)|(d,PC,Xn)|imm|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|✓||✓|✓|✓|✓|✓|✓|✓||||

