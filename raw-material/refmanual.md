##### Integer Instructions

##### 4-

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# ABCD

## Add Decimal with Extend

# ABCD

#### (M68000 Family)

#### Operation:

#### Source10 + Destination10 + X

#### →

#### Destination

#### Assembler

#### ABCD Dy,Dx

#### Syntax:

#### ABCD – (Ay), – (Ax)

#### Attributes:

#### Size = (Byte)

#### Description:

#### Adds the source operand to the destination operand along with the extend bit,

#### and stores the result in the destination location. The addition is performed using binary-

#### coded decimal arithmetic. The operands, which are packed binary-coded decimal

#### numbers, can be addressed in two different ways:

#### 1. Data Register to Data Register: The operands are contained in the data regis-

#### ters specified in the instruction.

#### 2. Memory to Memory: The operands are addressed with the predecrement ad-

#### dressing mode using the address registers specified in the instruction.

#### This operation is a byte operation only.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Undefined.

#### Z — Cleared if the result is nonzero; unchanged otherwise.

#### V — Undefined.

#### C — Set if a decimal carry was generated; cleared otherwise.

#### NOTE

#### Normally, the Z condition code bit is set via programming before

#### the start of an operation. This allows successful tests for zero

#### results upon completion of multiple-precision operations.

###### X N Z V C

```
*
```
###### U

```
*
```
###### U

```
*
```

##### Integer Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 4-

# ABCD

## Add Decimal with Extend

# ABCD

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Register Rx field—Specifies the destination register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

#### R/M field—Specifies the operand addressing mode.

#### 0 — The operation is data register to data register.

#### 1 — The operation is memory to memory.

#### Register Ry field—Specifies the source register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1100 REGISTER Rx 1 0 0 0 0 R/M REGISTER Ry
```

##### Integer Instructions

##### 4-

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# ADD

## Add

# ADD

#### (M68000 Family)

#### Operation:

#### Source + Destination

#### →

#### Destination

#### Assembler

#### ADD < ea > ,Dn

#### Syntax:

#### ADD Dn, < ea >

#### Attributes:

#### Size = (Byte, Word, Long)

#### Description:

#### Adds the source operand to the destination operand using binary addition and

#### stores the result in the destination location. The size of the operation may be specified

#### as byte, word, or long. The mode of the instruction indicates which operand is the

#### source and which is the destination, as well as the operand size.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow is generated; cleared otherwise.

#### C — Set if a carry is generated; cleared otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1101 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 4-

# ADD

## Add

# ADD

#### (M68000 Family)

#### Instruction Fields:

#### Register field—Specifies any of the eight data registers.

#### Opmode field

#### Effective Address field—Determines addressing mode.

#### a. If the location specified is a source operand, all addressing modes can be used

#### as listed in the following tables:

```
*Word and long only
**Can be used with CPU32.
```
#### Byte Word Long Operation

#### 000 001 010 < ea > + Dn

#### →

#### Dn

#### 100 101 110 Dn + < ea >

#### →

#### < ea >

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d
16
,An) 101 reg. number:An (d
16

###### ,PC) 111 010

```
(d
8
,An,Xn) 110 reg. number:An (d
8
,PC,Xn) 111 011
```
##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# ADD

## Add

# ADD

#### (M68000 Family)

#### b. If the location specified is a destination operand, only memory alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU
```
#### NOTE

#### The Dn mode is used when the destination is a data register; the

#### destination < ea > mode is invalid for a data register.

#### ADDA is used when the destination is an address register. ADDI

#### and ADDQ are used when the source is immediate data. Most

#### assemblers automatically make this distinction.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d
16
,An) 101 reg. number:An (d
16

###### ,PC) — —

```
(d
8
,An,Xn) 110 reg. number:An (d
8
,PC,Xn) — —
```
##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 4-

# ADDA

## Add Address

# ADDA

#### (M68000 Family)

#### Operation:

#### Source + Destination

#### →

#### Destination

#### Assembler

#### Syntax:

#### ADDA < ea > , An

#### Attributes:

#### Size = (Word, Long)

#### Description:

#### Adds the source operand to the destination address register and stores the

#### result in the address register. The size of the operation may be specified as word or

#### long. The entire destination address register is used regardless of the operation size.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies any of the eight address registers. This is always the

#### destination.

#### Opmode field—Specifies the size of the operation.

#### 011— Word operation; the source operand is sign-extended to a long operand and

#### the operation is performed on the address register using all 32 bits.

#### 111— Long operation.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1101 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### 4-

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# ADDA

## Add Address

# ADDA

## (M68000 Family)

#### Effective Address field—Specifies the source operand. All addressing modes can be

#### used as listed in the following tables:

```
*Can be used with CPU
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d
16
,An) 101 reg. number:An (d
16

###### ,PC) 111 010

```
(d
8
,An,Xn) 110 reg. number:An (d
8
,PC,Xn) 111 011
```
##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 4-

# ADDI

## Add Immediate

# ADDI

#### (M68000 Family)

#### Operation:

#### Immediate Data + Destination → Destination

#### Assembler

#### Syntax: ADDI # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Adds the immediate data to the destination operand and stores the result in

#### the destination location. The size of the operation may be specified as byte, word, or

#### long. The size of the immediate data matches the operation size.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow is generated; cleared otherwise.

#### C — Set if a carry is generated; cleared otherwise.

#### Instruction Format:

###### X N Z V C

###### *****^

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00000110 SIZE MODEEFFECTIVE ADDRESS REGISTER
16-BIT WORD DATA 8-BIT BYTE DATA
32-BIT LONG DATA
```

##### Integer Instructions

##### 4-10 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ADDI Add Immediate ADDI

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU
```
#### Immediate field—Data immediately following the instruction.

#### If size = 00, the data is the low-order byte of the immediate word.

#### If size = 01, the data is the entire immediate word.

#### If size = 10, the data is the next two immediate words.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-

# ADDQ Add Quick ADDQ

#### (M68000 Family)

#### Operation: Immediate Data + Destination → Destination

#### Assembler

#### Syntax: ADDQ # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Adds an immediate value of one to eight to the operand at the destination

#### location. The size of the operation may be specified as byte, word, or long. Word and

#### long operations are also allowed on the address registers. When adding to address

#### registers, the condition codes are not altered, and the entire destination address

#### register is used regardless of the operation size.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a carry occurs; cleared otherwise.

#### The condition codes are not affected when the destination is an address register.

#### Instruction Format:

###### X N Z V C

###### *****^

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 1 DATA 0 SIZE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### 4-12 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ADDQ Add Quick ADDQ

#### (M68000 Family)

#### Instruction Fields:

#### Data field—Three bits of immediate data representing eight values (0 – 7), with the

#### immediate value zero representing a value of eight.

#### Size field—Specifies the size of the operation.

#### 00— Byte operation

#### 01— Word operation

#### 10— Long operation

#### Effective Address field—Specifies the destination location. Only alterable addressing

#### modes can be used as listed in the following tables:

```
*Word and long only.
**Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn** 110 reg. number:An (bd,PC,Xn)† — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-

# ADDX Add Extended ADDX

#### (M68000 Family)

#### Operation: Source + Destination + X → Destination

#### Assembler ADDX Dy,Dx

#### Syntax: ADDX – (Ay), – (Ax)

#### Attributes: Size = (Byte, Word, Long)

#### Description: Adds the source operand and the extend bit to the destination operand and

#### stores the result in the destination location. The operands can be addressed in two

#### different ways:

#### 1. Data register to data register—The data registers specified in the instruction

#### contain the operands.

#### 2. Memory to memory—The address registers specified in the instruction address

#### the operands using the predecrement addressing mode.

#### The size of the operation can be specified as byte, word, or long.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Cleared if the result is nonzero; unchanged otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a carry is generated; cleared otherwise.

#### NOTE

#### Normally, the Z condition code bit is set via programming before

#### the start of an operation. This allows successful tests for zero

#### results upon completion of multiple-precision operations.

###### X N Z V C

###### *****^


##### Integer Instructions

##### 4-14 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ADDX Add Extended ADDX

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Register Rx field—Specifies the destination register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### R/M field—Specifies the operand address mode.

#### 0 — The operation is data register to data register.

#### 1 — The operation is memory to memory.

#### Register Ry field—Specifies the source register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1101 REGISTER Rx 1 SIZE 0 0 R/M REGISTER Ry
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-

# AND AND Logical AND

#### (M68000 Family)

#### Operation: Source L Destination → Destination

#### Assembler AND < ea > ,Dn

#### Syntax: AND Dn, < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Performs an AND operation of the source operand with the destination

#### operand and stores the result in the destination location. The size of the operation can

#### be specified as byte, word, or long. The contents of an address register may not be

#### used as an operand.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies any of the eight data registers.

#### Opmode field

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1100 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```
#### Byte Word Long Operation

#### 000 001 010 < ea > Λ Dn → Dn

#### 100 101 110 Dn Λ < ea > → < ea >


##### Integer Instructions

##### 4-16 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# AND AND Logical AND

#### (M68000 Family)

#### Effective Address field—Determines addressing mode.

#### a. If the location specified is a source operand, only data addressing modes can be

#### used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-

# AND AND Logical AND

#### (M68000 Family)

#### b. If the location specified is a destination operand, only memory alterable address-

#### ing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### The Dn mode is used when the destination is a data register; the

#### destination < ea > mode is invalid for a data register.

#### Most assemblers use ANDI when the source is immediate data.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-18 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ANDI AND Immediate ANDI

#### (M68000 Family)

#### Operation: Immediate Data Λ Destination → Destination

#### Assembler

#### Syntax: ANDI # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Performs an AND operation of the immediate data with the destination

#### operand and stores the result in the destination location. The size of the operation can

#### be specified as byte, word, or long. The size of the immediate data matches the

#### operation size.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00000010 SIZE MODEEFFECTIVE ADDRESS REGISTER
16-BIT WORD DATA 8-BIT BYTE DATA
32-BIT LONG DATA
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-

# ANDI AND Immediate ANDI

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU
```
#### Immediate field—Data immediately following the instruction.

#### If size = 00, the data is the low-order byte of the immediate word.

#### If size = 01, the data is the entire immediate word.

#### If size = 10, the data is the next two immediate words.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-20 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ANDI ANDI

# to CCR CCR AND Immediate to CCR

#### (M68000 Family)

#### Operation: Source Λ CCR → CCR

#### Assembler

#### Syntax: ANDI # < data > ,CCR

#### Attributes: Size = (Byte)

#### Description: Performs an AND operation of the immediate operand with the condition

#### codes and stores the result in the low-order byte of the status register.

#### Condition Codes:

#### X — Cleared if bit 4 of immediate operand is zero; unchanged otherwise.

#### N — Cleared if bit 3 of immediate operand is zero; unchanged otherwise.

#### Z — Cleared if bit 2 of immediate operand is zero; unchanged otherwise.

#### V — Cleared if bit 1 of immediate operand is zero; unchanged otherwise.

#### C — Cleared if bit 0 of immediate operand is zero; unchanged otherwise.

#### Instruction Format:

###### X N Z V C

###### *****^

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 0 0 1 0 0 0 1 1 1 1 0 0
00000000 8-BIT BYTE DATA
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-

# ASL, ASR Arithmetic Shift ASL, ASR

#### (M68000 Family)

#### Operation: Destination Shifted By Count → Destination

#### Assembler ASd Dx,Dy

#### Syntax: ASd # < data > ,Dy

#### ASd < ea >

#### where d is direction, L or R

#### Attributes: Size = (Byte, Word, Long)

#### Description: Arithmetically shifts the bits of the operand in the direction (L or R) specified.

#### The carry bit receives the last bit shifted out of the operand. The shift count for the

#### shifting of a register may be specified in two different ways:

#### 1. Immediate—The shift count is specified in the instruction (shift range, 1 – 8).

#### 2. Register—The shift count is the value in the data register specified in instruction

#### modulo 64.

#### The size of the operation can be specified as byte, word, or long. An operand in mem-

#### ory can be shifted one bit only, and the operand size is restricted to a word.

#### For ASL, the operand is shifted left; the number of positions shifted is the shift count.

#### Bits shifted out of the high-order bit go to both the carry and the extend bits; zeros are

#### shifted into the low-order bit. The overflow bit indicates if any sign changes occur dur-

#### ing the shift.

#### .

```
C OPERAND O
```
```
X
```
```
ASL:
```

##### Integer Instructions

##### 4-22 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ASL, ASR Arithmetic Shift ASL, ASR

#### (M68000 Family)

#### For ASR, the operand is shifted right; the number of positions shifted is the shift count.

#### Bits shifted out of the low-order bit go to both the carry and the extend bits; the sign bit

#### (MSB) is shifted into the high-order bit.

#### Condition Codes:

#### X — Set according to the last bit shifted out of the operand; unaffected for a shift

#### count of zero.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if the most significant bit is changed at any time during the shift operation;

#### cleared otherwise.

#### C — Set according to the last bit shifted out of the operand; cleared for a shift count

#### of zero.

#### Instruction Format:

##### REGISTER SHIFTS

#### Instruction Fields:

#### Count/Register field—Specifies shift count or register that contains the shift count:

#### If i/r = 0, this field contains the shift count. The values 1 – 7 represent counts of 1 –

#### 7; a value of zero represents a count of eight.

#### If i/r = 1, this field specifies the data register that contains the shift count (modulo 64).

###### X N Z V C

###### *****^

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110) REGISTERCOUNT? dr SIZE i/r 0 0 REGISTER
OPERAND C
X
ASR:
MSB


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-23

# ASL, ASR Arithmetic Shift ASL, ASR

#### (M68000 Family)

#### dr field—Specifies the direction of the shift.

#### 0 — Shift right

#### 1 — Shift left

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### i/r field

#### If i/r = 0, specifies immediate shift count.

#### If i/r = 1, specifies register shift count.

#### Register field—Specifies a data register to be shifted.

#### Instruction Format:

##### MEMORY SHIFTS

#### Instruction Fields:

#### dr field—Specifies the direction of the shift.

#### 0 — Shift right

#### 1 — Shift left

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1 1 1 0 0 0 0 dr (^11) MODEEFFECTIVE ADDRESS REGISTER


##### Integer Instructions

##### 4-24 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ASL, ASR Arithmetic Shift ASL, ASR

#### (M68000 Family)

#### Effective Address field—Specifies the operand to be shifted. Only memory alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-25

# Bcc Branch Conditionally Bcc

#### (M68000 Family)

#### Operation: If Condition True

#### Then PC + dn → PC

#### Assembler

#### Syntax: Bcc < label >

#### Attributes: Size = (Byte, Word, Long*)

##### *(MC68020, MC68030, and MC68040 only)

#### Description: If the specified condition is true, program execution continues at location (PC)

#### + displacement. The program counter contains the address of the instruction word for

#### the Bcc instruction plus two. The displacement is a twos-complement integer that

#### represents the relative distance in bytes from the current program counter to the

#### destination program counter. If the 8-bit displacement field in the instruction word is

#### zero, a 16-bit displacement (the word immediately following the instruction) is used. If

#### the 8-bit displacement field in the instruction word is all ones ($FF), the 32-bit

#### displacement (long word immediately following the instruction) is used. Condition code

#### cc specifies one of the following conditional tests (refer to Table 3-19 for more

#### information on these conditional tests):

#### Condition Codes:

#### Not affected.

##### Mnemonic Condition Mnemonic Condition

```
CC(HI) Carry Clear LS Low or Same
CS(LO) Carry Set LT Less Than
EQ Equal MI Minus
GE Greater or Equal NE Not Equal
GT Greater Than PL Plus
HI High VC Overflow Clear
LE Less or Equal VS Overflow Set
```

##### Integer Instructions

##### 4-26 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# Bcc Branch Conditionally Bcc

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Condition field—The binary code for one of the conditions listed in the table.

#### 8-Bit Displacement field—Twos complement integer specifying the number of bytes

#### between the branch instruction and the next instruction to be executed if the

#### condition is met.

#### 16-Bit Displacement field—Used for the displacement when the 8-bit displacement

#### field contains $00.

#### 32-Bit Displacement field—Used for the displacement when the 8-bit displacement

#### field contains $FF.

#### NOTE

#### A branch to the immediately following instruction automatically

#### uses the 16-bit displacement format because the 8-bit

#### displacement field contains $00 (zero offset).

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0110 CONDITION 8-BIT DISPLACEMENT
16-BIT DISPLACEMENT IF 8-BIT DISPLACEMENT = $00
32-BIT DISPLACEMENT IF 8-BIT DISPLACEMENT = $FF
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-27

# BCHG Test a Bit and Change BCHG

#### (M68000 Family)

#### Operation: TEST ( < number > of Destination) → Z;

#### TEST ( < number > of Destination) → < bit number > of Destination

#### Assembler BCHG Dn, < ea >

#### Syntax: BCHG # < data > , < ea >

#### Attributes: Size = (Byte, Long)

#### Description: Tests a bit in the destination operand and sets the Z condition code

#### appropriately, then inverts the specified bit in the destination. When the destination is

#### a data register, any of the 32 bits can be specified by the modulo 32-bit number. When

#### the destination is a memory location, the operation is a byte operation, and the bit

#### number is modulo 8. In all cases, bit zero refers to the least significant bit. The bit

#### number for this operation may be specified in either of two ways:

#### 1. Immediate—The bit number is specified in a second word of the instruction.

#### 2. Register—The specified data register contains the bit number.

#### Condition Codes:

#### X — Not affected.

#### N — Not affected.

#### Z — Set if the bit tested is zero; cleared otherwise.

#### V — Not affected.

#### C — Not affected.

###### X N Z V C

###### ——* — —


##### Integer Instructions

##### 4-28 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BCHG Test a Bit and Change BCHG

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER DYNAMIC, SPECIFIED IN A REGISTER

#### Instruction Fields:

#### Register field—Specifies the data register that contains the bit number.

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Long only; all others are byte only.
**Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0000 REGISTER (^101) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-29

# BCHG Test a Bit and Change BCHG

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER STATIC, SPECIFIED AS IMMEDIATE DATA

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Long only; all others are byte only.
**Can be used with CPU32.
```
#### Bit Number field—Specifies the bit number.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0000100001) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 0 0 0 0 BIT NUMBER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† — (bd,An,Xn)**
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — ([bd,An,Xn],od)
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — ([bd,An],Xn,od)
```

##### Integer Instructions

##### 4-30 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BCLR Test a Bit and Clear BCLR

#### (M68000 Family)

#### Operation: TEST ( < bit number > of Destination) → Z; 0 → < bit number > of Des-

#### tination

#### Assembler BCLR Dn, < ea >

#### Syntax: BCLR # < data > , < ea >

#### Attributes: Size = (Byte, Long)

#### Description: Tests a bit in the destination operand and sets the Z condition code

#### appropriately, then clears the specified bit in the destination. When a data register is

#### the destination, any of the 32 bits can be specified by a modulo 32-bit number. When

#### a memory location is the destination, the operation is a byte operation, and the bit

#### number is modulo 8. In all cases, bit zero refers to the least significant bit. The bit

#### number for this operation can be specified in either of two ways:

#### 1. Immediate—The bit number is specified in a second word of the instruction.

#### 2. Register—The specified data register contains the bit number.

#### Condition Codes:

#### X — Not affected.

#### N — Not affected.

#### Z — Set if the bit tested is zero; cleared otherwise.

#### V — Not affected.

#### C — Not affected.

###### X N Z V C

###### ——* — —


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-31

# BCLR Test a Bit and Clear BCLR

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER DYNAMIC, SPECIFIED IN A REGISTER

#### Instruction Fields:

#### Register field—Specifies the data register that contains the bit number.

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Long only; all others are byte only.
**Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0000 REGISTER (^110) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-32 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BCLR Test a Bit and Clear BCLR

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER STATIC, SPECIFIED AS IMMEDIATE DATA

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Long only; all others are byte only.
**Can be used with CPU32.
```
#### Bit Number field—Specifies the bit number.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0000100010) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 0 0 0 0 BIT NUMBER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-33

# BFCHG Test Bit Field and Change BFCHG

#### (MC68020, MC68030, MC68040)

#### Operation: TEST ( < bit field > of Destination) → < bit field > of Destination

#### Assembler

#### Syntax: BFCHG < ea > {offset:width}

#### Attributes: Unsized

#### Description: Sets the condition codes according to the value in a bit field at the specified

#### effective address, then complements the field.

#### A field offset and a field width select the field. The field offset specifies the starting bit

#### of the field. The field width determines the number of bits in the field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

#### NOTE

#### For the MC68020, MC68030, and MC68040, all bit field

#### instructions access only those bytes in memory that contain

#### some portion of the bit field. The possible accesses are byte,

#### word, 3-byte, long word, and long word with byte (for a 5-byte

#### access).

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110101011) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 Do OFFSET Dw WIDTH


##### Integer Instructions

##### 4-34 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFCHG Test Bit Field and Change BFCHG

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control alterable addressing modes can be used as listed in the following

#### table:

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 3 – 4 are zero.

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand; an operand value in the range 1

- 31 specifies a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-35

# BFCLR Test Bit Field and Clear BFCLR

#### (MC68020, MC68030, MC68040)

#### Operation: 0 → < bit field > of Destination

#### Assembler

#### Syntax: BFCLR < ea > {offset:width}

#### Attributes: Unsized

#### Description: Sets condition codes according to the value in a bit field at the specified

#### effective address and clears the field.

#### The field offset and field width select the field. The field offset specifies the starting bit

#### of the field. The field width determines the number of bits in the field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110110011) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 Do OFFSET Dw WIDTH


##### Integer Instructions

##### 4-36 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFCLR Test Bit Field and Clear BFCLR

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control alterable addressing modes can be used as listed in the following

#### table:

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### of 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 3 – 4 are zero.

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand; operand values in the range of 1

- 31 specify a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-37

# BFEXTS Extract Bit Field Signed BFEXTS

#### (MC68020, MC68030, MC68040)

#### Operation: < bit field > of Source → Dn

#### Assembler

#### Syntax: BFEXTS < ea > {offset:width},Dn

#### Attributes: Unsized

#### Description: Extracts a bit field from the specified effective address location, sign extends

#### to 32 bits, and loads the result into the destination data register. The field offset and

#### field width select the bit field. The field offset specifies the starting bit of the field. The

#### field width determines the number of bits in the field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110101111) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Do OFFSET Dw WIDTH


##### Integer Instructions

##### 4-38 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFEXTS Extract Bit Field Signed BFEXTS

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control addressing modes can be used as listed in the following table:

#### Register field—Specifies the destination register.

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### of 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 4 – 3 are zero.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-39

# BFEXTS Extract Bit Field Signed BFEXTS

#### (MC68020, MC68030, MC68040)

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand; operand values in the range of 1

- 31 specify a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.


##### Integer Instructions

##### 4-40 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFEXTU Extract Bit Field Unsigned BFEXTU

#### (MC68020, MC68030, MC68040)

#### Operation: < bit offset > of Source → Dn

#### Assembler

#### Syntax: BFEXTU < ea > {offset:width},Dn

#### Attributes: Unsized

#### Description: Extracts a bit field from the specified effective address location, zero extends

#### to 32 bits, and loads the results into the destination data register. The field offset and

#### field width select the field. The field offset specifies the starting bit of the field. The field

#### width determines the number of bits in the field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the source field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110100111) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Do OFFSET Dw WIDTH


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-41

# BFEXTU Extract Bit Field Unsigned BFEXTU

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control addressing modes can be used as listed in the following table:

#### Register field—Specifies the destination data register.

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### of 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 4 – 3 are zero.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Integer Instructions

##### 4-42 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFEXTU Extract Bit Field Unsigned BFEXTU

#### (MC68020, MC68030, MC68040)

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand; operand values in the range of 1

- 31 specify a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-43

# BFFFO Find First One in Bit Field BFFFO

#### (MC68020, MC68030, MC68040)

#### Operation: < bit offset > of Source Bit Scan → Dn

#### Assembler

#### Syntax: BFFFO < ea > {offset:width},Dn

#### Attributes: Unsized

#### Description: Searches the source operand for the most significant bit that is set to a value

#### of one. The bit offset of that bit (the bit offset in the instruction plus the offset of the first

#### one bit) is placed in Dn. If no bit in the bit field is set to one, the value in Dn is the field

#### offset plus the field width. The instruction sets the condition codes according to the bit

#### field value. The field offset and field width select the field. The field offset specifies the

#### starting bit of the field. The field width determines the number of bits in the field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110100111) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Do OFFSET Dw WIDTH


##### Integer Instructions

##### 4-44 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFFFO Find First One in Bit Field BFFFO

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control addressing modes can be used as listed in the following table:

#### Register field—Specifies the destination data register operand.

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### of 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 4 – 3 are zero.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-45

# BFFFO Find First One in Bit Field BFFFO

#### (MC68020, MC68030, MC68040)

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand; operand values in the range of 1

- 31 specify a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.


##### Integer Instructions

##### 4-46 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFINS Insert Bit Field BFINS

#### (MC68020, MC68030, MC68040)

#### Operation: Dn → < bit field > of Destination

#### Assembler

#### Syntax: BFINS Dn, < ea > {offset:width}

#### Attributes: Unsized

#### Description: Inserts a bit field taken from the low-order bits of the specified data register

#### into a bit field at the effective address location. The instruction sets the condition codes

#### according to the inserted value. The field offset and field width select the field. The field

#### offset specifies the starting bit of the field. The field width determines the number of bits

#### in the field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110111111) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Do OFFSET Dw WIDTH


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-47

# BFINS Insert Bit Field BFINS

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control alterable addressing modes can be used as listed in the following

#### table:

#### Register field—Specifies the source data register operand.

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### of 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 4 – 3 are zero.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Integer Instructions

##### 4-48 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFINS Insert Bit Field BFINS

#### (MC68020, MC68030, MC68040)

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand; operand values in the range of 1

- 31 specify a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-49

# BFSET Test Bit Field and Set BFSET

#### (MC68020, MC68030, MC68040)

#### Operation: 1 → < bit field > of Destination

#### Assembler

#### Syntax: BFSET < ea > {offset:width}

#### Attributes: Unsized

#### Description: Sets the condition codes according to the value in a bit field at the specified

#### effective address, then sets each bit in the field.

#### The field offset and the field width select the field. The field offset specifies the starting

#### bit of the field. The field width determines the number of bits in the field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ** 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110111011) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 Do OFFSET Dw WIDTH


##### Integer Instructions

##### 4-50 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFSET Test Bit Field and Set BFSET

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control alterable addressing modes can be used as listed in the following

#### table:

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### of 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 4 – 3 are zero.

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand; operand values in the range of 1

- 31 specify a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-51

# BFTST Test Bit Field BFTST

#### (MC68020, MC68030, MC68040)

#### Operation: < bit field > of Destination

#### Assembler

#### Syntax: BFTST < ea > {offset:width}

#### Attributes: Unsized

#### Description: Sets the condition codes according to the value in a bit field at the specified

#### effective address location. The field offset and field width select the field. The field offset

#### specifies the starting bit of the field. The field width determines the number of bits in the

#### field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the field is set; cleared otherwise.

#### Z — Set if all bits of the field are zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110100011) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 Do OFFSET Dw WIDTH


##### Integer Instructions

##### 4-52 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BFTST Test Bit Field BFTST

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Effective Address field—Specifies the base location for the bit field. Only data register

#### direct or control addressing modes can be used as listed in the following table:

#### Do field—Determines how the field offset is specified.

#### 0 — The offset field contains the bit field offset.

#### 1 — Bits 8 – 6 of the extension word specify a data register that contains the offset;

#### bits 10 – 9 are zero.

#### Offset field—Specifies the field offset, depending on Do.

#### If Do = 0, the offset field is an immediate operand; the operand value is in the range

#### of 0 – 31.

#### If Do = 1, the offset field specifies a data register that contains the offset. The value

#### is in the range of – 2^31 to 2^31 – 1.

#### Dw field—Determines how the field width is specified.

#### 0 — The width field contains the bit field width.

#### 1 — Bits 2 – 0 of the extension word specify a data register that contains the width;

#### bits 4 – 3 are zero.

#### Width field—Specifies the field width, depending on Dw.

#### If Dw = 0, the width field is an immediate operand, operand values in the range of 1

- 31 specify a field width of 1 – 31, and a value of zero specifies a width of 32.

#### If Dw = 1, the width field specifies a data register that contains the width. The value

#### is modulo 32; values of 1 – 31 specify field widths of 1 – 31, and a value of zero

#### specifies a width of 32.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-53

# BKPT Breakpoint BKPT

#### (MC68EC000, MC68010, MC68020, MC68030, MC68040, CPU32)

#### Operation: Run Breakpoint Acknowledge Cycle; TRAP As Illegal Instruction

#### Assembler

#### Syntax: BKPT # < data >

#### Attributes: Unsized

#### Description: For the MC68010, a breakpoint acknowledge bus cycle is run with function

#### codes driven high and zeros on all address lines. Whether the breakpoint acknowledge

#### bus cycle is terminated with DTACK, BERR, or VPA, the processor always takes an

#### illegal instruction exception. During exception processing, a debug monitor can

#### distinguish different software breakpoints by decoding the field in the BKPT instruction.

#### For the MC68000 and MC68008, the breakpoint cycle is not run, but an illegal

#### instruction exception is taken.

#### For the MC68020, MC68030, and CPU32, a breakpoint acknowledge bus cycle is exe-

#### cuted with the immediate data (value 0 – 7) on bits 2 – 4 of the address bus and zeros

#### on bits 0 and 1 of the address bus. The breakpoint acknowledge bus cycle accesses

#### the CPU space, addressing type 0, and provides the breakpoint number specified by

#### the instruction on address lines A2 – A4. If the external hardware terminates the cycle

#### with DSACKx or STERM, the data on the bus (an instruction word) is inserted into the

#### instruction pipe and is executed after the breakpoint instruction. The breakpoint instruc-

#### tion requires a word to be transferred so, if the first bus cycle accesses an 8- bit port,

#### a second bus cycle is required. If the external logic terminates the breakpoint acknowl-

#### edge bus cycle with BERR (i.e., no instruction word available), the processor takes an

#### illegal instruction exception.

#### For the MC68040, this instruction executes a breakpoint acknowledge bus cycle.

#### Regardless of the cycle termination, the MC68040 takes an illegal instruction excep-

#### tion.

#### For more information on the breakpoint instruction refer to the appropriate user’s man-

#### ual on bus operation.

#### This instruction supports breakpoints for debug monitors and real- time hardware emu-

#### lators.


##### Integer Instructions

##### 4-54 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BKPT Breakpoint BKPT

#### (MC68EC000, MC68010, MC68020,

#### MC68030, MC68040, CPU32)

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Field:

#### Vector field—Contains the immediate data, a value in the range of 0 – 7. This is the

#### breakpoint number.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0100100001001 VECTOR
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-55

# BRA Branch Always BRA

#### (M68000 Family)

#### Operation: PC + dn → PC

#### Assembler

#### Syntax: BRA < label >

#### Attributes: Size = (Byte, Word, Long*)

##### *(MC68020, MC68030, MC68040 only)

#### Description: Program execution continues at location (PC) + displacement. The program

#### counter contains the address of the instruction word of the BRA instruction plus two.

#### The displacement is a twos complement integer that represents the relative distance in

#### bytes from the current program counter to the destination program counter. If the 8-bit

#### displacement field in the instruction word is zero, a 16-bit displacement (the word

#### immediately following the instruction) is used. If the 8-bit displacement field in the

#### instruction word is all ones ($FF), the 32-bit displacement (long word immediately

#### following the instruction) is used.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### 8-Bit Displacement field—Twos complement integer specifying the number of bytes

#### between the branch instruction and the next instruction to be executed.

#### 16-Bit Displacement field—Used for a larger displacement when the 8-bit displacement

#### is equal to $00.

#### 32-Bit Displacement field—Used for a larger displacement when the 8-bit displacement

#### is equal to $FF.

#### NOTE

#### A branch to the immediately following instruction automatically

#### uses the 16-bit displacement format because the 8-bit

#### displacement field contains $00 (zero offset).

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
01100000 8-BIT DISPLACEMENT
16-BIT DISPLACEMENT IF 8-BIT DISPLACEMENT = $00
32-BIT DISPLACEMENT IF 8-BIT DISPLACEMENT = $FF
```

##### Integer Instructions

##### 4-56 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BSET Test a Bit and Set BSET

#### (M68000 Family)

#### Operation: TEST ( < bit number > of Destination) → Z; 1 → < bit number > of Des-

#### tination

#### Assembler BSET Dn, < ea >

#### Syntax: BSET # < data > , < ea >

#### Attributes: Size = (Byte, Long)

#### Description: Tests a bit in the destination operand and sets the Z condition code

#### appropriately, then sets the specified bit in the destination operand. When a data

#### register is the destination, any of the 32 bits can be specified by a modulo 32-bit

#### number. When a memory location is the destination, the operation is a byte operation,

#### and the bit number is modulo 8. In all cases, bit zero refers to the least significant bit.

#### The bit number for this operation can be specified in either of two ways:

#### 1. Immediate—The bit number is specified in the second word of the instruction.

#### 2. Register—The specified data register contains the bit number.

#### Condition Codes:

#### X — Not affected.

#### N — Not affected.

#### Z — Set if the bit tested is zero; cleared otherwise.

#### V — Not affected.

#### C — Not affected.

###### X N Z V C

###### ——∗ — —


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-57

# BSET Test a Bit and Set BSET

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER DYNAMIC, SPECIFIED IN A REGISTER

#### Instruction Fields:

#### Register field—Specifies the data register that contains the bit number.

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Long only; all others are byte only.
**Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0000 REGISTER (^111) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-58 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BSET Test a Bit and Set BSET

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER STATIC, SPECIFIED AS IMMEDIATE DATA

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Long only; all others are byte only.
**Can be used with CPU32.
```
#### Bit Number field—Specifies the bit number.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0000100011) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 0 0 0 BIT NUMBER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-59

# BSR Branch to Subroutine BSR

#### (M68000 Family)

#### Operation: SP – 4 → SP; PC → (SP); PC + dn → PC

#### Assembler

#### Syntax: BSR < label >

#### Attributes: Size = (Byte, Word, Long*)

##### *(MC68020, MC68030, MC68040 only)

#### Description: Pushes the long-word address of the instruction immediately following the

#### BSR instruction onto the system stack. The program counter contains the address of

#### the instruction word plus two. Program execution then continues at location (PC) +

#### displacement. The displacement is a twos complement integer that represents the

#### relative distance in bytes from the current program counter to the destination program

#### counter. If the 8-bit displacement field in the instruction word is zero, a 16-bit

#### displacement (the word immediately following the instruction) is used. If the 8-bit

#### displacement field in the instruction word is all ones ($FF), the 32-bit displacement

#### (long word immediately following the instruction) is used.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
01100001 8-BIT DISPLACEMENT
16-BIT DISPLACEMENT IF 8-BIT DISPLACEMENT = $00
32-BIT DISPLACEMENT IF 8-BIT DISPLACEMENT = $FF
```

##### Integer Instructions

##### 4-60 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BSR Branch to Subroutine BSR

#### (M68000 Family)

#### Instruction Fields:

#### 8-Bit Displacement field—Twos complement integer specifying the number of bytes

#### between the branch instruction and the next instruction to be executed.

#### 16-Bit Displacement field—Used for a larger displacement when the 8-bit displacement

#### is equal to $00.

#### 32-Bit Displacement field—Used for a larger displacement when the 8-bit displacement

#### is equal to $FF.

#### NOTE

#### A branch to the immediately following instruction automatically

#### uses the 16-bit displacement format because the 8-bit

#### displacement field contains $00 (zero offset).


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-61

# BTST Test a Bit BTST

#### (M68000 Family)

#### Operation: TEST ( < bit number > of Destination) → Z

#### Assembler BTST Dn, < ea >

#### Syntax: BTST # < data > , < ea >

#### Attributes: Size = (Byte, Long)

#### Description: Tests a bit in the destination operand and sets the Z condition code

#### appropriately. When a data register is the destination, any of the 32 bits can be

#### specified by a modulo 32- bit number. When a memory location is the destination, the

#### operation is a byte operation, and the bit number is modulo 8. In all cases, bit zero

#### refers to the least significant bit. The bit number for this operation can be specified in

#### either of two ways:

#### 1. Immediate—The bit number is specified in a second word of the instruction.

#### 2. Register—The specified data register contains the bit number.

#### Condition Codes:

#### X — Not affected.

#### N — Not affected.

#### Z — Set if the bit tested is zero; cleared otherwise.

#### V — Not affected.

#### C — Not affected.

###### X N Z V C

###### ——∗ — —


##### Integer Instructions

##### 4-62 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# BTST Test a Bit BTST

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER DYNAMIC, SPECIFIED IN A REGISTER

#### Instruction Fields:

#### Register field—Specifies the data register that contains the bit number.

#### Effective Address field—Specifies the destination location. Only data addressing

#### modes can be used as listed in the following tables:

```
*Long only; all others are byte only.
**Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0000 REGISTER (^100) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-63

# BTST Test a Bit BTST

#### (M68000 Family)

#### Instruction Format:

##### BIT NUMBER STATIC, SPECIFIED AS IMMEDIATE DATA

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only data addressing

#### modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### Bit Number field—Specifies the bit number.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0000100000) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 0 0 0 0 BIT NUMBER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-64 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CALLM Call Module CALLM

#### (MC68020)

#### Operation: Save Current Module State on Stack; Load New Module State from

#### Destination

#### Assembler

#### Syntax: CALLM # < data > , < ea >

#### Attributes: Unsized

#### Description: The effective address of the instruction is the location of an external module

#### descriptor. A module frame is created on the top of the stack, and the current module

#### state is saved in the frame. The immediate operand specifies the number of bytes of

#### arguments to be passed to the called module. A new module state is loaded from the

#### descriptor addressed by the effective address.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0000011011) MODEEFFECTIVE ADDRESS REGISTER
00000000 ARGUMENT COUNT


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-65

# CALLM Call Module CALLM

#### (MC68020)

#### Instruction Fields:

#### Effective Address field—Specifies the address of the module descriptor. Only control

#### addressing modes can be used as listed in the following table:

#### Argument Count field—Specifies the number of bytes of arguments to be passed to the

#### called module. The 8-bit field can specify from 0 to 255 bytes of arguments. The

#### same number of bytes is removed from the stack by the RTM instruction.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Integer Instructions

##### 4-66 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CAS CAS

# CAS2 Compare and Swap with Operand CAS2

#### (MC68020, MC68030, MC68040)

#### Operation: CAS Destination – Compare Operand → cc;

#### If Z, Update Operand → Destination

#### Else Destination → Compare Operand

#### CAS2 Destination 1 – Compare 1 → cc;

#### If Z, Destination 2 – Compare 2 → cc

#### If Z, Update 1 → Destination 1; Update 2 → Destination 2

#### Else Destination 1 → Compare 1; Destination 2 → Compare 2

#### Assembler CAS Dc,Du, < ea >

#### Syntax: CAS2 Dc1:Dc2,Du1:Du2,(Rn1):(Rn2)

#### Attributes: Size = (Byte * , Word, Long)

#### Description: CAS compares the effective address operand to the compare operand (Dc).

#### If the operands are equal, the instruction writes the update operand (Du) to the effective

#### address operand; otherwise, the instruction writes the effective address operand to the

#### compare operand (Dc).

#### CAS2 compares memory operand 1 (Rn1) to compare operand 1 (Dc1). If the oper-

#### ands are equal, the instruction compares memory operand 2 (Rn2) to compare oper-

#### and 2 (Dc2). If these operands are also equal, the instruction writes the update

#### operands (Du1 and Du2) to the memory operands (Rn1 and Rn2). If either comparison

#### fails, the instruction writes the memory operands (Rn1 and Rn2) to the compare oper-

#### ands (Dc1 and Dc2).

#### Both operations access memory using locked or read-modify-write transfer sequences,

#### providing a means of synchronizing several processors.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow is generated; cleared otherwise.

#### C — Set if a borrow is generated; cleared otherwise.

##### *. CAS2 cannot use byte operands.

###### X N Z V C

###### — ∗∗∗∗


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-67

# CAS CAS

# CAS2 Compare and Swap with Operand CAS2

#### (MC68020, MC68030, MC68040)

#### Instruction Format:

##### CAS

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 01 — Byte operation

#### 10 — Word operation

#### 11 — Long operation

#### Effective Address field—Specifies the location of the memory operand. Only memory

#### alterable addressing modes can be used as listed in the following table:

#### Du field—Specifies the data register that contains the update value to be written to the

#### memory operand location if the comparison is successful.

#### Dc field—Specifies the data register that contains the value to be compared to the

#### memory operand.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
00001 SIZE (^011) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 0 0 0 0 Du 0 0 0 Dc

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Integer Instructions

##### 4-68 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CAS CAS

# CAS2 Compare and Swap with Operand CAS2

#### (MC68020, MC68030, MC68040)

#### Instruction Format:

##### CAS2

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 10 — Word operation

#### 11 — Long operation

#### D/A1, D/A2 fields—Specify whether Rn1 and Rn2 reference data or address registers,

#### respectively.

#### 0 — The corresponding register is a data register.

#### 1 — The corresponding register is an address register.

#### Rn1, Rn2 fields—Specify the numbers of the registers that contain the addresses of

#### the first and second memory operands, respectively. If the operands overlap in

#### memory, the results of any memory update are undefined.

#### Du1, Du2 fields—Specify the data registers that contain the update values to be written

#### to the first and second memory operand locations if the comparison is successful.

#### Dc1, Dc2 fields—Specify the data registers that contain the test values to be compared

#### to the first and second memory operands, respectively. If Dc1 and Dc2 specify the

#### same data register and the comparison fails, memory operand 1 is stored in the

#### data register.

#### NOTE

#### The CAS and CAS2 instructions can be used to perform secure

#### update operations on system control data structures in a

#### multiprocessing environment.

#### In the MC68040 if the operands are not equal, the destination or

#### destination 1 operand is written back to memory to complete the

#### locked access for CAS or CAS2, respectively.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00001 SIZE 0 1 1 1 1 1 1 0 0
D/A1 Rn1 0 0 0 Du1 0 0 0 Dc1
D/A2 Rn2 0 0 0 Du2 0 0 0 Dc2
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-69

# CHK Check Register Against Bounds CHK

#### (M68000 Family)

#### Operation: If Dn < 0 or Dn > Source

#### Then TRAP

#### Assembler

#### Syntax: CHK < ea > ,Dn

#### Attributes: Size = (Word, Long*)

##### *(MC68020, MC68030, MC68040 only)

#### Description: Compares the value in the data register specified in the instruction to zero and

#### to the upper bound (effective address operand). The upper bound is a twos

#### complement integer. If the register value is less than zero or greater than the upper

#### bound, a CHK instruction exception (vector number 6) occurs.

#### Condition Codes:

#### X — Not affected.

#### N — Set if Dn < 0; cleared if Dn > effective address operand; undefined otherwise.

#### Z — Undefined.

#### V — Undefined.

#### C — Undefined.

#### Instruction Format:

###### X N Z V C

###### — ∗ U U U

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0100 REGISTER SIZE (^0) MODEEFFECTIVE ADDRESS REGISTER


##### Integer Instructions

##### 4-70 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CHK Check Register Against Bounds CHK

#### (M68000 Family)

#### Instruction Fields:

#### Register field—Specifies the data register that contains the value to be checked.

#### Size field—Specifies the size of the operation.

#### 11 — Word operation

#### 10— Long operation

#### Effective Address field—Specifies the upper bound operand. Only data addressing

#### modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-71

# CHK2 Check Register Against Bounds CHK2

#### (MC68020, MC68030, MC68040, CPU32)

#### Operation: If Rn < LB or Rn > UB

#### Then TRAP

#### Assembler

#### Syntax: CHK2 < ea > ,Rn

#### Attributes: Size = (Byte, Word, Long)

#### Description: Compares the value in Rn to each bound. The effective address contains the

#### bounds pair: the upper bound following the lower bound. For signed comparisons, the

#### arithmetically smaller value should be used as the lower bound. For unsigned

#### comparisons, the logically smaller value should be the lower bound.

#### The size of the data and the bounds can be specified as byte, word, or long. If Rn is a

#### data register and the operation size is byte or word, only the appropriate low-order part

#### of Rn is checked. If Rn is an address register and the operation size is byte or word,

#### the bounds operands are sign-extended to 32 bits, and the resultant operands are

#### compared to the full 32 bits of An.

#### If the upper bound equals the lower bound, the valid range is a single value. If the reg-

#### ister value is less than the lower bound or greater than the upper bound, a CHK instruc-

#### tion exception (vector number 6) occurs.

#### Condition Codes:

#### X — Not affected.

#### N — Undefined.

#### Z — Set if Rn is equal to either bound; cleared otherwise.

#### V — Undefined.

#### C — Set if Rn is out of bounds; cleared otherwise.

###### X N Z V C

###### —U∗ U ∗


##### Integer Instructions

##### 4-72 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CHK2 Check Register Against Bounds CHK2

#### (MC68020, MC68030, MC68040, CPU32)

#### Instruction Format:

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the location of the bounds operands. Only control

#### addressing modes can be used as listed in the following tables:

#### D/A field—Specifies whether an address register or data register is to be checked.

#### 0 — Data register

#### 1 — Address register

#### Register field—Specifies the address or data register that contains the value to be

#### checked.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
00000 SIZE (^011) MODEEFFECTIVE ADDRESS REGISTER
D/A REGISTER 1 0 0 0 0 0 0 0 0 0 0 0

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-73

# CLR Clear an Operand CLR

#### (M68000 Family)

#### Operation: 0 → Destination

#### Assembler

#### Syntax: CLR < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Clears the destination operand to zero. The size of the operation may be

#### specified as byte, word, or long.

#### Condition Codes:

#### X — Not affected.

#### N — Always cleared.

#### Z — Always set.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — 0 1 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
01000010 SIZE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### 4-74 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CLR Clear an Operand CLR

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00— Byte operation

#### 01— Word operation

#### 10— Long operation

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### In the MC68000 and MC68008 a memory location is read before

#### it is cleared.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-75

# CMP Compare CMP

#### (M68000 Family)

#### Operation: Destination – Source → cc

#### Assembler

#### Syntax: CMP < ea > , Dn

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the source operand from the destination data register and sets the

#### condition codes according to the result; the data register is not changed. The size of

#### the operation can be byte, word, or long.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a borrow occurs; cleared otherwise.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies the destination data register.

#### Opmode field

###### X N Z V C

###### — ∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1011 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```
#### Byte Word Long Operation

#### 000 001 010 Dn – < ea >


##### Integer Instructions

##### 4-76 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CMP Compare CMP

#### (M68000 Family)

#### Effective Address field—Specifies the source operand. All addressing modes can be

#### used as listed in the following tables:

```
*Word and Long only.
**Can be used with CPU32.
```
#### NOTE

#### CMPA is used when the destination is an address register. CMPI

#### is used when the source is immediate data. CMPM is used for

#### memory-to-memory compares. Most assemblers automatically

#### make the distinction.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-77

# CMPA Compare Address CMPA

#### (M68000 Family)

#### Operation: Destination – Source → cc

#### Assembler

#### Syntax: CMPA < ea > , An

#### Attributes: Size = (Word, Long)

#### Description: Subtracts the source operand from the destination address register and sets

#### the condition codes according to the result; the address register is not changed. The

#### size of the operation can be specified as word or long. Word length source operands

#### are sign- extended to 32 bits for comparison.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow is generated; cleared otherwise.

#### C — Set if a borrow is generated; cleared otherwise.

#### Instruction Format:

###### X N Z V C

###### — ∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1011 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### 4-78 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CMPA Compare Address CMPA

#### (M68000 Family)

#### Instruction Fields:

#### Register field—Specifies the destination address register.

#### Opmode field—Specifies the size of the operation.

#### 011— Word operation; the source operand is sign-extended to a long operand, and

#### the operation is performed on the address register using all 32 bits.

#### 111— Long operation.

#### Effective Address field—Specifies the source operand. All addressing modes can be

#### used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-79

# CMPI Compare Immediate CMPI

#### (M68000 Family)

#### Operation: Destination – Immediate Data → cc

#### Assembler

#### Syntax: CMPI # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the immediate data from the destination operand and sets the

#### condition codes according to the result; the destination location is not changed. The

#### size of the operation may be specified as byte, word, or long. The size of the immediate

#### data matches the operation size.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a borrow occurs; cleared otherwise.

#### Instruction Format:

###### X N Z V C

###### — ∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00001100 SIZE MODEEFFECTIVE ADDRESS REGISTER
16-BIT WORD DATA 8-BIT BYTE DATA
32-BIT LONG DATA
```

##### Integer Instructions

##### 4-80 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CMPI Compare Immediate CMPI

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the destination operand. Only data addressing

#### modes can be used as listed in the following tables:

```
*PC relative addressing modes do not apply to MC68000, MC680008, or MC6801.
**Can be used with CPU32.
```
#### Immediate field—Data immediately following the instruction.

#### If size = 00, the data is the low-order byte of the immediate word.

#### If size = 01, the data is the entire immediate word.

#### If size = 10, the data is the next two immediate words.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC)* 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn)* 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)† 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-81

# CMPM Compare Memory CMPM

#### (M68000 Family)

#### Operation: Destination – Source → cc

#### Assembler

#### Syntax: CMPM (Ay) + ,(Ax) +

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the source operand from the destination operand and sets the

#### condition codes according to the results; the destination location is not changed. The

#### operands are always addressed with the postincrement addressing mode, using the

#### address registers specified in the instruction. The size of the operation may be

#### specified as byte, word, or long.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow is generated; cleared otherwise.

#### C — Set if a borrow is generated; cleared otherwise.

#### Instruction Format:

#### Instruction Fields:

#### Register Ax field—(always the destination) Specifies an address register in the

#### postincrement addressing mode.

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Register Ay field—(always the source) Specifies an address register in the

#### postincrement addressing mode.

###### X N Z V C

###### — ∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1011 REGISTER Ax 1 SIZE 0 0 1 REGISTER Ay
```

##### Integer Instructions

##### 4-82 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# CMP2 Compare Register Against Bounds CMP2

#### (MC68020, MC68030, MC68040, CPU32)

#### Operation: Compare Rn < LB or Rn > UB and Set Condition Codes

#### Assembler

#### Syntax: CMP2 < ea > ,Rn

#### Attributes: Size = (Byte, Word, Long)

#### Description: Compares the value in Rn to each bound. The effective address contains the

#### bounds pair: upper bound following the lower bound. For signed comparisons, the

#### arithmetically smaller value should be used as the lower bound. For unsigned

#### comparisons, the logically smaller value should be the lower bound.

#### The size of the data and the bounds can be specified as byte, word, or long. If Rn is a

#### data register and the operation size is byte or word, only the appropriate low-order part

#### of Rn is checked. If Rn is an address register and the operation size is byte or word,

#### the bounds operands are sign-extended to 32 bits, and the resultant operands are

#### compared to the full 32 bits of An.

#### If the upper bound equals the lower bound, the valid range is a single value.

#### NOTE

#### This instruction is identical to CHK2 except that it sets condition

#### codes rather than taking an exception when the value in Rn is

#### out of bounds.

#### Condition Codes:

#### X — Not affected.

#### N — Undefined.

#### Z — Set if Rn is equal to either bound; cleared otherwise.

#### V — Undefined.

#### C — Set if Rn is out of bounds; cleared otherwise.

###### X N Z V C

###### —U∗ U ∗


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-83

# CMP2 Compare Register Against Bounds CMP2

#### (MC68020, MC68030, MC68040, CPU32)

#### Instruction Format:

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the location of the bounds pair. Only control

#### addressing modes can be used as listed in the following tables:

#### D/A field—Specifies whether an address register or data register is compared.

#### 0 — Data register

#### 1 — Address register

#### Register field—Specifies the address or data register that contains the value to be

#### checked.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
00000 SIZE (^011) MODEEFFECTIVE ADDRESS REGISTER
D/A REGISTER 0 0 0 0 0 0 0 0 0 0 0 0

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-84 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# cpBcc Branch on Coprocessor Condition cpBcc

#### (MC68020, MC68030)

#### Operation: If cpcc True

#### Then Scan PC + dn → PC

#### Assembler

#### Syntax: cpBcc < label >

#### Attributes: Size = (Word, Long)

#### Description: If the specified coprocessor condition is true, program execution continues at

#### location scan PC + displacement. The value of the scan PC is the address of the first

#### displacement word. The displacement is a twos complement integer that represents

#### the relative distance in bytes from the scan PC to the destination program counter. The

#### displacement can be either 16 or 32 bits. The coprocessor determines the specific

#### condition from the condition field in the operation word.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Identifies the coprocessor for this operation. Coprocessor ID of

#### 000 results in an F-line exception for the MC68030.

#### Size field—Specifies the size of the displacement.

#### 0 — The displacement is 16 bits.

#### 1 — The displacement is 32 bits.

#### Coprocessor Condition field—Specifies the coprocessor condition to be tested. This

#### field is passed to the coprocessor, which provides directives to the main

#### processor for processing this instruction.

#### 16-Bit Displacement field—The displacement value occupies 16 bits.

#### 32-Bit Displacement field—The displacement value occupies 32 bits.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111 COPROCESSORID 0 1 SIZE COPROCESSOR CONDITION
OPTIONAL COPROCESSOR-DEFINED EXTENSION WORDS
WORD OR
LONG-WORD DISPLACEMENT
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-85

# cpDBcc Test Coprocessor Condition cpDBcc

#### Decrement and Branch

#### (MC68020, MC68030)

#### Operation: If cpcc False

#### Then (Dn – 1 → Dn; If Dn ≠ – 1 Then Scan PC + dn → PC)

#### Assembler

#### Syntax: cpDBcc Dn, < label >

#### Attributes: Size = (Word)

#### Description: If the specified coprocessor condition is true, execution continues with the

#### next instruction. Otherwise, the low-order word in the specified data register is

#### decremented by one. If the result is equal to – 1, execution continues with the next

#### instruction. If the result is not equal to – 1, execution continues at the location indicated

#### by the value of the scan PC plus the sign-extended 16-bit displacement. The value of

#### the scan PC is the address of the displacement word. The displacement is a twos

#### complement integer that represents the relative distance in bytes from the scan PC to

#### the destination program counter. The coprocessor determines the specific condition

#### from the condition word that follows the operation word.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Identifies the coprocessor for this operation; coprocessor ID of

#### 000 results in an F-line exception for the MC68030.

#### Register field—Specifies the data register used as the counter.

#### Coprocessor Condition field—Specifies the coprocessor condition to be tested. This

#### field is passed to the coprocessor, which provides directives to the main

#### processor for processing this instruction.

#### Displacement field—Specifies the distance of the branch (in bytes).

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111 COPROCESSORID 001001 REGISTER
0000000000 COPROCESSOR CONDITION
OPTIONAL COPROCESSOR-DEFINED EXTENSION WORDS
16-BIT DISPLACEMENT
```

##### Integer Instructions

##### 4-86 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# cpGEN Coprocessor General Function cpGEN

#### (MC68020, MC68030)

#### Operation: Pass Command Word to Coprocessor

#### Assembler

#### Syntax: cpGEN < parameters as defined by coprocessor >

#### Attributes: Unsized

#### Description: Transfers the command word that follows the operation word to the specified

#### coprocessor. The coprocessor determines the specific operation from the command

#### word. Usually a coprocessor defines specific instances of this instruction to provide its

#### instruction set.

#### Condition Codes:

#### May be modified by coprocessor; unchanged otherwise.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Identifies the coprocessor for this operation; note that

#### coprocessor ID of 000 is reserved for MMU instructions for the MC68030.

#### Effective Address field—Specifies the location of any operand not resident in the

#### coprocessor. The allowable addressing modes are determined by the operation

#### to be performed.

#### Coprocessor Command field—Specifies the coprocessor operation to be performed.

#### This word is passed to the coprocessor, which in turn provides directives to the

#### main processor for processing this instruction.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
COPROCESSOR-DEPENDENT COMMAND WORD
OPTIONAL EFFECTIVE ADDRESS OR COPROCESSOR-DEFINED EXTENSIONWORDS


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-87

# cpScc Set on Coprocessor Condition cpScc

#### (MC68020, MC68030)

#### Operation: If cpcc True

#### Then 1s → Destination

#### Else 0s → Destination

#### Assembler

#### Syntax: cpScc < ea >

#### Attributes: Size = (Byte)

#### Description: Tests the specified coprocessor condition code. If the condition is true, the

#### byte specified by the effective address is set to TRUE (all ones); otherwise, that byte is

#### set to FALSE (all zeros). The coprocessor determines the specific condition from the

#### condition word that follows the operation word.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^001) MODEEFFECTIVE ADDRESS REGISTER
0000000000 COPROCESSOR CONDITION
OPTIONAL EFFECTIVE ADDRESS OR COPROCESSOR-DEFINED EXTENSIONWORDS


##### Integer Instructions

##### 4-88 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# cpScc Set on Coprocessor Condition cpScc

#### (MC68020, MC68030)

#### Instruction Fields:

#### Coprocessor ID field—Identifies the coprocessor for this operation. Coprocessor ID of

#### 000 results in an F-line exception for the MC68030.

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following table:

#### Coprocessor Condition field—Specifies the coprocessor condition to be tested. This

#### field is passed to the coprocessor, which in turn provides directives to the main

#### processor for processing this instruction.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-89

# cpTRAPcc Trap on Coprocessor Condition cpTRAPcc

#### (MC68020, MC68030)

#### Operation: If cpcc True

#### Then TRAP

#### Assembler cpTRAPcc

#### Syntax: cpTRAPcc # < data >

#### Attributes: Unsized or Size = (Word, Long)

#### Description: Tests the specified coprocessor condition code; if the selected coprocessor

#### condition is true, the processor initiates a cpTRAPcc exception, vector number 7. The

#### program counter value placed on the stack is the address of the next instruction. If the

#### selected condition is not true, no operation is performed, and execution continues with

#### the next instruction. The coprocessor determines the specific condition from the

#### condition word that follows the operation word. Following the condition word is a user-

#### defined data operand specified as immediate data to be used by the trap handler.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Identifies the coprocessor for this operation; coprocessor ID of

#### 000 results in an F-line exception for the MC68030.

#### Opmode field—Selects the instruction form.

#### 010— Instruction is followed by one operand word.

#### 011— Instruction is followed by two operand words.

#### 100— Instruction has no following operand words.

#### Coprocessor Condition field—Specifies the coprocessor condition to be tested. This

#### field is passed to the coprocessor, which provides directives to the main

#### processor for processing this instruction.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111 COPROCESSORID 001111 OPMODE
0000000000 COPROCESSOR CONDITION
OPTIONAL COPROCESSOR-DEFINED EXTENSION WORDS
OPTIONAL WORD
OR LONG-WORD OPERAND
```

##### Integer Instructions

##### 4-90 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# DBcc Test Condition, Decrement, and Branch DBcc

#### (M68000 Family)

#### Operation: If Condition False

#### Then (Dn – 1 → Dn; If Dn ≠ – 1 Then PC + dn → PC)

#### Assembler

#### Syntax: DBcc Dn, < label >

#### Attributes: Size = (Word)

#### Description: Controls a loop of instructions. The parameters are a condition code, a data

#### register (counter), and a displacement value. The instruction first tests the condition for

#### termination; if it is true, no operation is performed. If the termination condition is not

#### true, the low-order 16 bits of the counter data register decrement by one. If the result

#### is – 1, execution continues with the next instruction. If the result is not equal to – 1,

#### execution continues at the location indicated by the current value of the program

#### counter plus the sign-extended 16-bit displacement. The value in the program counter

#### is the address of the instruction word of the DBcc instruction plus two. The

#### displacement is a twos complement integer that represents the relative distance in

#### bytes from the current program counter to the destination program counter. Condition

#### code cc specifies one of the following conditional tests (refer to Table 3-19 for more

#### information on these conditional tests):

#### Condition Codes:

#### Not affected.

```
Mnemonic Condition Mnemonic Condition
CC(HI) Carry Clear LS Low or Same
CS(LO) Carry Set LT Less Than
EQ Equal MI Minus
F False NE Not Equal
GE Greater or Equal PL Plus
GT Greater Than T True
HI High VC Overflow Clear
LE Less or Equal VS Overflow Set
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-91

# DBcc Test Condition, Decrement, and Branch DBcc

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Condition field—The binary code for one of the conditions listed in the table.

#### Register field—Specifies the data register used as the counter.

#### Displacement field—Specifies the number of bytes to branch.

#### NOTE

#### The terminating condition is similar to the UNTIL loop clauses of

#### high-level languages. For example: DBMI can be stated as

#### "decrement and branch until minus".

#### Most assemblers accept DBRA for DBF for use when only a

#### count terminates the loop (no condition is tested).

#### A program can enter a loop at the beginning or by branching to

#### the trailing DBcc instruction. Entering the loop at the beginning

#### is useful for indexed addressing modes and dynamically

#### specified bit operations. In this case, the control index count

#### must be one less than the desired number of loop executions.

#### However, when entering a loop by branching directly to the

#### trailing DBcc instruction, the control count should equal the loop

#### execution count. In this case, if a zero count occurs, the DBcc

#### instruction does not branch, and the main loop is not executed.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0101 CONDITION 11001 REGISTER
16-BIT DISPLACEMENT
```

##### Integer Instructions

##### 4-92 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# DIVS, DIVSL Signed Divide DIVS, DIVSL

#### (M68000 Family)

#### Operation: Destination ÷ Source → Destination

#### Assembler DIVS.W < ea > ,Dn32/16 → 16r – 16q

#### Syntax: *DIVS.L < ea > ,Dq 32/32 → 32q

#### *DIVS.L < ea > ,Dr:Dq 64/32 → 32r – 32q

#### *DIVSL.L < ea > ,Dr:Dq 32/32 → 32r – 32q

##### *Applies to MC68020, MC68030, MC68040, CPU32 only

#### Attributes: Size = (Word, Long)

#### Description: Divides the signed destination operand by the signed source operand and

#### stores the signed result in the destination. The instruction uses one of four forms. The

#### word form of the instruction divides a long word by a word. The result is a quotient in

#### the lower word (least significant 16 bits) and a remainder in the upper word (most

#### significant 16 bits). The sign of the remainder is the same as the sign of the dividend.

#### The first long form divides a long word by a long word. The result is a long quotient; the

#### remainder is discarded.

#### The second long form divides a quad word (in any two data registers) by a long word.

#### The result is a long-word quotient and a long-word remainder.

#### The third long form divides a long word by a long word. The result is a long-word quo-

#### tient and a long-word remainder.

#### Two special conditions may arise during the operation:

#### 1. Division by zero causes a trap.

#### 2. Overflow may be detected and set before the instruction completes. If the in-

#### struction detects an overflow, it sets the overflow condition code, and the oper-

#### ands are unaffected.

#### Condition Codes:

#### X—Not affected.

#### N — Set if the quotient is negative; cleared otherwise; undefined if overflow or divide

#### by zero occurs.

#### Z — Set if the quotient is zero; cleared otherwise; undefined if overflow or divide by

#### zero occurs.

#### V — Set if division overflow occurs; undefined if divide by zero occurs; cleared oth-

#### erwise.

#### C — Always cleared.

###### X N Z V C

###### — ∗∗∗ 0


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-93

# DIVS, DIVSL Signed Divide DIVS, DIVSL

#### (M68000 Family)

#### Instruction Format:

##### WORD

#### Instruction Fields:

#### Register field—Specifies any of the eight data registers. This field always specifies the

#### destination operand.

#### Effective Address field—Specifies the source operand. Only data alterable addressing

#### modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### Overflow occurs if the quotient is larger than a 16-bit signed

#### integer.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1000 REGISTER (^111) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-94 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# DIVS, DIVSL Signed Divide DIVS, DIVSL

#### (M68000 Family)

#### Instruction Format:

##### LONG

#### Instruction Fields:

#### Effective Address field—Specifies the source operand. Only data alterable addressing

#### modes can be used as listed in the following tables:

#### Register Dq field—Specifies a data register for the destination operand. The low-order

#### 32 bits of the dividend comes from this register, and the 32-bit quotient is loaded

#### into this register.

#### Size field—Selects a 32- or 64-bit division operation.

#### 0 — 32-bit dividend is in register Dq.

#### 1 — 64-bit dividend is in Dr – Dq.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100110001) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Dq 1 SIZE 0000000 REGISTER Dr

##### MC68020, MC68030, and MC68040 only

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-95

# DIVS, DIVSL Signed Divide DIVS, DIVSL

#### (M68000 Family)

#### Register Dr field—After the division, this register contains the 32-bit remainder. If Dr

#### and Dq are the same register, only the quotient is returned. If the size field is 1,

#### this field also specifies the data register that contains the high-order 32 bits of the

#### dividend.

#### NOTE

#### Overflow occurs if the quotient is larger than a 32-bit signed

#### integer.


##### Integer Instructions

##### 4-96 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# DIVU, DIVUL Unsigned Divide DIVU, DIVUL

#### (M68000 Family)

#### Operation: Destination ÷ Source → Destination

#### Assembler DIVU.W < ea > ,Dn32/16 → 16r – 16q

#### Syntax: *DIVU.L < ea > ,Dq 32/32 → 32q

#### *DIVU.L < ea > ,Dr:Dq 64/32 → 32r – 32q

#### *DIVUL.L < ea > ,Dr:Dq 32/32 → 32r – 32q

##### *Applies to MC68020, MC68030, MC68040, CPU32 only.

#### Attributes: Size = (Word, Long)

#### Description: Divides the unsigned destination operand by the unsigned source

#### operand and stores the unsigned result in the destination. The instruction uses one of

#### four forms. The word form of the instruction divides a long word by a word. The result

#### is a quotient in the lower word (least significant 16 bits) and a remainder in the upper

#### word (most significant 16 bits).

#### The first long form divides a long word by a long word. The result is a long quotient; the

#### remainder is discarded.

#### The second long form divides a quad word (in any two data registers) by a long word.

#### The result is a long-word quotient and a long-word remainder.

#### The third long form divides a long word by a long word. The result is a long-word quo-

#### tient and a long-word remainder.

#### Two special conditions may arise during the operation:

#### 1. Division by zero causes a trap.

#### 2. Overflow may be detected and set before the instruction completes. If the in-

#### struction detects an overflow, it sets the overflow condition code, and the oper-

#### ands are unaffected.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the quotient is negative; cleared otherwise; undefined if overflow or divide

#### by zero occurs.

#### Z — Set if the quotient is zero; cleared otherwise; undefined if overflow or divide by

#### zero occurs.

#### V — Set if division overflow occurs; cleared otherwise; undefined if divide by zero

#### occurs.

#### C — Always cleared.

###### X N Z V C

###### — ∗∗∗ 0


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-97

# DIVU, DIVUL Unsigned Divide DIVU, DIVUL

#### (M68000 Family)

#### Instruction Format:

##### WORD

#### Instruction Fields:

#### Register field—Specifies any of the eight data registers; this field always specifies the

#### destination operand.

#### Effective Address field—Specifies the source operand. Only data addressing modes

#### can be used as listed in the following tables:

```
**Can be used with CPU32.
```
#### NOTE

#### Overflow occurs if the quotient is larger than a 16-bit signed

#### integer.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1000 REGISTER (^011) MODEEFFECTIVE ADDRESS REGISTER

##### MC68020, MC68030, and MC68040 only

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-98 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# DIVU, DIVUL Unsigned Divide DIVU, DIVUL

#### (M68000 Family)

#### Instruction Format:

##### LONG

#### Instruction Fields:

#### Effective Address field—Specifies the source operand. Only data addressing modes

#### can be used as listed in the following tables:

#### Register Dq field—Specifies a data register for the destination operand. The low-order

#### 32 bits of the dividend comes from this register, and the 32-bit quotient is loaded

#### into this register.

#### Size field—Selects a 32- or 64-bit division operation.

#### 0 — 32-bit dividend is in register Dq.

#### 1 — 64-bit dividend is in Dr – Dq.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100110001) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Dq 0 SIZE 0000000 REGISTER Dr

##### MC68020, MC68030, and MC68040 only

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011

##### MC68020, MC68030, and MC68040 only

```
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-99

# DIVU, DIVUL Unsigned Divide DIVU, DIVUL

#### (M68000 Family)

#### Register Dr field—After the division, this register contains the 32-bit remainder. If Dr

#### and Dq are the same register, only the quotient is returned. If the size field is 1,

#### this field also specifies the data register that contains the high-order 32 bits of the

#### dividend.

#### NOTE

#### Overflow occurs if the quotient is larger than a 32-bit unsigned

#### integer.


##### Integer Instructions

##### 4-100 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# EOR Exclusive-OR Logical EOR

#### (M68000 Family)

#### Operation: Source ⊕ Destination → Destination

#### Assembler

#### Syntax: EOR Dn, < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Performs an exclusive-OR operation on the destination operand using the

#### source operand and stores the result in the destination location. The size of the

#### operation may be specified to be byte, word, or long. The source operand must be a

#### data register. The destination operand is specified in the effective address field.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

##### WORD

#### Instruction Fields:

#### Register field—Specifies any of the eight data registers.

#### Opmode field

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1011 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```
#### Byte Word Long Operation

#### 100 101 110 < ea > ⊕ Dn → < ea >


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-101

# EOR Exclusive-OR Logical EOR

#### (M68000 Family)

#### Effective Address field—Specifies the destination ope data alterable addressing modes

#### can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### Memory-to-data-register operations are not allowed. Most

#### assemblers use EORI when the source is immediate data.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-102 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# EORI Exclusive-OR Immediate EORI

#### (M68000 Family)

#### Operation: Immediate Data ⊕ Destination → Destination

#### Assembler

#### Syntax: EORI # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Performs an exclusive-OR operation on the destination operand using the

#### immediate data and the destination operand and stores the result in the destination

#### location. The size of the operation may be specified as byte, word, or long. The size of

#### the immediate data matches the operation size.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00001010 SIZE MODEEFFECTIVE ADDRESS REGISTER
16-BIT WORD DATA 8-BIT BYTE DATA
32-BIT LONG DATA
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-103

# EORI Exclusive-OR Immediate EORI

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00— Byte operation

#### 01— Word operation

#### 10— Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### Immediate field—Data immediately following the instruction.

#### If size = 00, the data is the low-order byte of the immediate word.

#### If size = 01, the data is the entire immediate word.

#### If size = 10, the data is next two immediate words.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-104 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# EORI EORI

# to CCR Exclusive-OR Immediate to CCR

## to Condition Code

#### (M68000 Family)

#### Operation: Source ⊕ CCR → CCR

#### Assembler

#### Syntax: EORI # < data > ,CCR

#### Attributes: Size = (Byte)

#### Description: Performs an exclusive-OR operation on the condition code register using the

#### immediate operand and stores the result in the condition code register (low-order byte

#### of the status register). All implemented bits of the condition code register are affected.

#### Condition Codes:

#### X — Changed if bit 4 of immediate operand is one; unchanged otherwise.

#### N — Changed if bit 3 of immediate operand is one; unchanged otherwise.

#### Z — Changed if bit 2 of immediate operand is one; unchanged otherwise.

#### V — Changed if bit 1 of immediate operand is one; unchanged otherwise.

#### C — Changed if bit 0 of immediate operand is one; unchanged otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 1 0 1 0 0 0 1 1 1 1 0 0
00000000 8-BIT BYTE DATA
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-105

# EXG Exchange Registers EXG

#### (M68000 Family)

#### Operation: Rx ←→ Ry

#### Assembler EXG Dx,Dy

#### Syntax: EXG Ax,Ay EXG Dx,Ay

#### Attributes: Size = (Long)

#### Description: Exchanges the contents of two 32-bit registers. The instruction performs three

#### types of exchanges.

#### 1. Exchange data registers.

#### 2. Exchange address registers.

#### 3. Exchange a data register and an address register.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Register Rx field—Specifies either a data register or an address register depending on

#### the mode. If the exchange is between data and address registers, this field always

#### specifies the data register.

#### Opmode field—Specifies the type of exchange.

#### 01000—Data registers

#### 01001—Address registers

#### 10001—Data register and address register

#### Register Ry field—Specifies either a data register or an address register depending on

#### the mode. If the exchange is between data and address registers, this field always

#### specifies the address register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1100 REGISTER Rx 1 OPMODE REGISTER Ry
```

##### Integer Instructions

##### 4-106 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# EXT, EXTB Sign-Extend EXT, EXTB

#### (M68000 Family)

#### Operation: Destination Sign-Extended → Destination

#### Assembler EXT.W Dnextend byte to word

#### Syntax: EXT.L Dnextend word to long word

#### EXTB.L Dnextend byte to long word (MC68020, MC68030

#### MC68040, CPU32)

#### Attributes: Size = (Word, Long)

#### Description: Extends a byte in a data register to a word or a long word, or a word in a data

#### register to a long word, by replicating the sign bit to the left. If the operation extends a

#### byte to a word, bit 7 of the designated data register is copied to bits 15 – 8 of that data

#### register. If the operation extends a word to a long word, bit 15 of the designated data

#### register is copied to bits 31 – 16 of the data register. The EXTB form copies bit 7 of the

#### designated register to bits 31 – 8 of the data register.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

#### Instruction Fields:

#### Opmode field—Specifies the size of the sign-extension operation.

#### 010— Sign-extend low-order byte of data register to word.

#### 011— Sign-extend low-order word of data register to long.

#### 111— Sign-extend low-order byte of data register to long.

#### Register field—Specifies the data register is to be sign-extended.

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0100100 OPMODE 0 0 0 REGISTER
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-107

# ILLEGAL Take Illegal Instruction Trap ILLEGAL

#### (M68000 Family)

#### Operation: *SSP – 2 → SSP; Vector Offset → (SSP);

#### SSP – 4 → SSP; PC → (SSP);

#### SSP – 2 → SSP; SR → (SSP);

#### Illegal Instruction Vector Address → PC

##### *The MC68000 and MC68008 cannot write the vector offset

##### and format code to the system stack.

#### Assembler

#### Syntax: ILLEGAL

#### Attributes: Unsized

#### Description: Forces an illegal instruction exception, vector number 4. All other illegal

#### instruction bit patterns are reserved for future extension of the instruction set and

#### should not be used to force an exception.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 0 1 0 1 1 1 1 1 1 0 0
```

##### Integer Instructions

##### 4-108 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# JMP Jump JMP

#### (M68000 Family)

#### Operation: Destination Address → PC

#### Assembler

#### Syntax: JMP < ea >

#### Attributes: Unsized

#### Description: Program execution continues at the effective address specified by the

#### instruction. The addressing mode for the effective address must be a control

#### addressing mode.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Field:

#### Effective Address field—Specifies the address of the next instruction. Only control

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100111011) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-109

# JSR Jump to Subroutine JSR

#### (M68000 Family)

#### Operation: SP – 4 → Sp; PC → (SP); Destination Address → PC

#### Assembler

#### Syntax: JSR < ea >

#### Attributes: Unsized

#### Description: Pushes the long-word address of the instruction immediately following the

#### JSR instruction onto the system stack. Program execution then continues at the

#### address specified in the instruction.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Field:

#### Effective Address field—Specifies the address of the next instruction. Only control

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100111010) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-110 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# LEA Load Effective Address LEA

#### (M68000 Family)

#### Operation: < ea > → An

#### Assembler

#### Syntax: LEA < ea > ,An

#### Attributes: Size = (Long)

#### Description: Loads the effective address into the specified address register. All 32 bits of

#### the address register are affected by this instruction.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies the address register to be updated with the effective address.

#### Effective Address field—Specifies the address to be loaded into the address register.

#### Only control addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0100 REGISTER (^111) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-111

# LINK Link and Allocate LINK

#### (M68000 Family)

#### Operation: SP – 4 → SP; An → (SP); SP → An; SP + dn → SP

#### Assembler

#### Syntax: LINK An, # < displacement >

#### Attributes: Size = (Word, Long*)

##### *MC68020, MC68030, MC68040 and CPU32 only.

#### Description: Pushes the contents of the specified address register onto the stack. Then

#### loads the updated stack pointer into the address register. Finally, adds the

#### displacement value to the stack pointer. For word-size operation, the displacement is

#### the sign-extended word following the operation word. For long size operation, the

#### displacement is the long word following the operation word. The address register

#### occupies one long word on the stack. The user should specify a negative displacement

#### in order to allocate stack area.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

##### WORD

#### Instruction Format:

##### LONG

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0100111001010 REGISTER
WORD DISPLACEMENT
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0100100000001 REGISTER
HIGH-ORDER DISPLACEMENT
LOW-ORDER DISPLACEMENT
```

##### Integer Instructions

##### 4-112 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# LINK Link and Allocate LINK

#### (M68000 Family)

#### Instruction Fields:

#### Register field—Specifies the address register for the link.

#### Displacement field—Specifies the twos complement integer to be added to the stack

#### pointer.

#### NOTE

#### LINK and UNLK can be used to maintain a linked list of local data

#### and parameter areas on the stack for nested subroutine calls.


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-113

# LSL, LSR Logical Shift LSL, LSR

#### (M68000 Family)

#### Operation: Destination Shifted By Count → Destination

#### Assembler LSd Dx,Dy

#### Syntax: LSd # < data > ,Dy

#### LSd < ea >

#### where d is direction, L or R

#### Attributes: Size = (Byte, Word, Long)

#### Description: Shifts the bits of the operand in the direction specified (L or R). The carry bit

#### receives the last bit shifted out of the operand. The shift count for the shifting of a

#### register is specified in two different ways:

#### 1. Immediate—The shift count (1 – 8) is specified in the instruction.

#### 2. Register—The shift count is the value in the data register specified in the in-

#### struction modulo 64.

#### The size of the operation for register destinations may be specified as byte, word, or

#### long. The contents of memory, < ea > , can be shifted one bit only, and the operand

#### size is restricted to a word.

#### The LSL instruction shifts the operand to the left the number of positions specified as

#### the shift count. Bits shifted out of the high-order bit go to both the carry and the extend

#### bits; zeros are shifted into the low-order bit.

#### .

#### The LSR instruction shifts the operand to the right the number of positions specified as

#### the shift count. Bits shifted out of the low-order bit go to both the carry and the extend

#### bits; zeros are shifted into the high-order bit.

#### .

```
C OPERAND O
```
```
X
```
```
LSL:
```
```
O OPERAND C
```
```
X
```
```
LSR:
```

##### Integer Instructions

##### 4-114 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# LSL, LSR Logical Shift LSL, LSR

#### (M68000 Family)

#### Condition Codes:

#### X — Set according to the last bit shifted out of the operand; unaffected for a shift

#### count of zero.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Set according to the last bit shifted out of the operand; cleared for a shift count

#### of zero.

#### Instruction Format:

##### REGISTER SHIFTS

#### Instruction Fields:

#### Count/Register field

#### If i/r = 0, this field contains the shift count. The values 1 – 7 represent shifts of 1 – 7;

#### value of zero specifies a shift count of eight.

#### If i/r = 1, the data register specified in this field contains the shift count (modulo 64).

#### dr field—Specifies the direction of the shift.

#### 0 — Shift right

#### 1 — Shift left

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation i/r field

#### If i/r = 0, specifies immediate shift count.

#### If i/r = 1, specifies register shift count.

#### Register field—Specifies a data register to be shifted.

###### X N Z V C

###### ∗∗∗ 0 ∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110) REGISTERCOUNT/ dr SIZE i/r 0 1 REGISTER


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-115

# LSL, LSR Logical Shift LSL, LSR

#### (M68000 Family)

#### Instruction Format:

##### MEMORY SHIFTS

#### Instruction Fields:

#### dr field—Specifies the direction of the shift.

#### 0 — Shift right

#### 1 — Shift left

#### Effective Address field—Specifies the operand to be shifted. Only memory alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1 1 1 0 0 0 1 dr (^11) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-116 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVE Move Data from Source to Destination MOVE

#### (M68000 Family)

#### Operation: Source → Destination

#### Assembler

#### Syntax: MOVE < ea > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Moves the data at the source to the destination location and sets the condition

#### codes according to the data. The size of the operation may be specified as byte, word,

#### or long. Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

#### Instruction Fields:

#### Size field—Specifies the size of the operand to be moved.

#### 01 — Byte operation

#### 11 — Word operation

#### 10 — Long operation

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 SIZE REGISTERDESTINATION MODE MODE SOURCE REGISTER
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-117

# MOVE Move Data from Source to Destination MOVE

#### (M68000 Family)

#### Destination Effective Address field—Specifies the destination location. Only data

#### alterable addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-118 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVE Move Data from Source to Destination MOVE

#### (M68000 Family)

#### Source Effective Address field—Specifies the source operand. All addressing modes

#### can be used as listed in the following tables:

```
*For byte size operation, address register direct is not allowed.
**Can be used with CPU32.
```
#### NOTE

#### Most assemblers use MOVEA when the destination is an

#### address register.

#### MOVEQ can be used to move an immediate 8-bit value to a data

#### register.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)** 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-119

# MOVEA Move Address MOVEA

#### (M68000 Family)

#### Operation: Source → Destination

#### Assembler

#### Syntax: MOVEA < ea > ,An

#### Attributes: Size = (Word, Long)

#### Description: Moves the contents of the source to the destination address register. The size

#### of the operation is specified as word or long. Word-size source operands are sign-

#### extended to 32-bit quantities.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Size field—Specifies the size of the operand to be moved.

#### 11 — Word operation; the source operand is sign-extended to a long operand and

#### all 32 bits are loaded into the address register.

#### 10 — Long operation.

#### Destination Register field—Specifies the destination address register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0 0 SIZE DESTINATIONREGISTER (^001) MODE SOURCE REGISTER


##### Integer Instructions

##### 4-120 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVEA Move Address MOVEA

#### (M68000 Family)

#### Effective Address field—Specifies the location of the source operand. All addressing

#### modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-121

# MOVE MOVE

# from CCR Move from the from CCR

## Condition Code Register

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### Operation: CCR → Destination

#### Assembler

#### Syntax: MOVE CCR, < ea >

#### Attributes: Size = (Word)

#### Description: Moves the condition code bits (zero-extended to word size) to the destination

#### location. The operand size is a word. Unimplemented bits are read as zeros.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100001011) MODEEFFECTIVE ADDRESS REGISTER


##### Integer Instructions

##### 4-122 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVE MOVE

# from CCR Move from the from CCR

## Condition Code Register

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### Instruction Field:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### MOVE from CCR is a word operation. ANDI, ORI, and EORI to

#### CCR are byte operations.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-123

# MOVE MOVE

# to CCR Move to Condition Code Register to CCR

#### (M68000 Family)

#### Operation: Source → CCR

#### Assembler

#### Syntax: MOVE < ea > ,CCR

#### Attributes: Size = (Word)

#### Description: Moves the low-order byte of the source operand to the condition code register.

#### The upper byte of the source operand is ignored; the upper byte of the status register

#### is not altered.

#### Condition Codes:

#### X — Set to the value of bit 4 of the source operand.

#### N — Set to the value of bit 3 of the source operand.

#### Z — Set to the value of bit 2 of the source operand.

#### V — Set to the value of bit 1 of the source operand.

#### C — Set to the value of bit 0 of the source operand.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100010011) MODEEFFECTIVE ADDRESS REGISTER


##### Integer Instructions

##### 4-124 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVE MOVE

# to CCR Move to Condition Code Register to CCR

#### (M68000 Family)

#### Instruction Field:

#### Effective Address field—Specifies the location of the source operand. Only data

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### MOVE to CCR is a word operation. ANDI, ORI, and EORI to

#### CCR are byte operations.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-125

# MOVE MOVE

# from SR Move from the Status Register from SR

#### (MC68000, MC68008)

#### Operation: SR → Destination

#### Assembler

#### Syntax: MOVE SR, < ea >

#### Attributes: Size = (Word)

#### Description: Moves the data in the status register to the destination location. The

#### destination is word length. Unimplemented bits are read as zeros.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following table:

#### NOTE

#### Use the MOVE from CCR instruction to access only the

#### condition codes. Memory destination is read before it is written

#### to.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100000011) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —


##### Integer Instructions

##### 4-126 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVE16 Move 16-Byte Block MOVE16

#### (MC68040)

#### Operation: Source Block → Destination Block

#### Assembler MOVE16 (Ax) + ,(Ay) +

#### Syntax: MOVE16 (xxx).L,(An)

#### MOVE16 (xxx).L,(An) +

#### MOVE16 (An),(xxx).L

#### MOVE16 (An) + ,(xxx).L

#### Attributes: Size = (Line)

#### Description: Moves the source line to the destination line. The lines are aligned to 16-byte

#### boundaries. Applications for this instruction include coprocessor communications,

#### memory initialization, and fast block copy operations.

#### MOVE16 has two formats. The postincrement format uses the postincrement address-

#### ing mode for both source and destination; whereas, the absolute format specifies an

#### absolute long address for either the source or destination.

#### Line transfers are performed using burst reads and writes, which begin with the long

#### word pointed to by the effective address of the source and destination, respectively. An

#### address register used in the postincrement addressing mode is incremented by 16

#### after the transfer.

#### Example: MOVE16 (A0) + $FE802 A0 = $1400F

#### The line at address $14000 is read into a temporary holding register by a burst read

#### transfer starting with long-word $14000. Address values in A0 of $14000 – $1400F

#### cause the same line to be read, starting at different long words. The line is then written

#### to the line at address $FE800 beginning with long-word $FE800 after the instruction A0

#### contains $1401F.

#### Source line at $14000:

#### Destination line at $FE8000:

###### $14000 $14004 $14008 $1400C

###### LONG WORD 0 LONG WORD 1 LONG WORD 2 LONG WORD 3

###### $FE800 $FE804 $FE808 $FE80C

###### LONG WORD 0 LONG WORD 1 LONG WORD 2 LONG WORD 3


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-127

# MOVE16 Move 16-Byte Block MOVE16

#### (MC68040)

#### Condition Codes:

#### Not affected.

#### Instruction Format:

##### POSTINCREMENT SOURCE AND DESTINATION

#### Instruction Fields:

#### Register Ax—Specifies a source address register for the postincrement addressing

#### mode.

#### Register Ay—Specifies a destination address register for the postincrement

#### addressing mode.

#### Instruction Format:

#### Absolute Long Address Source or Destination

#### Instruction Fields:

#### Opmode field—Specifies the addressing modes used for source and destination:

#### Register Ay—Specifies an address register for the indirect and postincrement

#### addressing mode used as a source or destination.

#### 32-Bit Address field—Specifies the absolute address used as a source or destination.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111011000100 REGISTER Ax
1 REGISTER Ay 0 0 0 0 0 0 0 0 0 0 0 0
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
11110110000 OPMODE REGISTER Ay
HIGH-ORDER ADDRESS
LOW-ORDER ADDRESS
```
```
Opmode Source Destinati on Assembler Syntax
0 0 (Ay) + (xxx).L MOVE16 (Ay) + ,(xxx).L
0 1 (xxx).L (Ay) + MOVE16 (xxx).L,(Ay) +
1 0 (Ay) (xxx).L MOVE16 (Ay),(xxx).L
1 1 (xxx).L (Ay) MOVE16 (xxx).L,(Ay)
```

##### Integer Instructions

##### 4-128 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVEM Move Multiple Registers MOVEM

#### (M68000 Family)

#### Operation: Registers → Destination; Source → Registers

#### Assembler MOVEM < list > , < ea >

#### Syntax: MOVEM < ea > , < list >

#### Attributes: Size = (Word, Long)

#### Description: Moves the contents of selected registers to or from consecutive memory

#### locations starting at the location specified by the effective address. A register is

#### selected if the bit in the mask field corresponding to that register is set. The instruction

#### size determines whether 16 or 32 bits of each register are transferred. In the case of a

#### word transfer to either address or data registers, each word is sign-extended to 32 bits,

#### and the resulting long word is loaded into the associated register.

#### Selecting the addressing mode also selects the mode of operation of the MOVEM

#### instruction, and only the control modes, the predecrement mode, and the postincre-

#### ment mode are valid. If the effective address is specified by one of the control modes,

#### the registers are transferred starting at the specified address, and the address is incre-

#### mented by the operand length (2 or 4) following each transfer. The order of the regis-

#### ters is from D0 to D7, then from A0 to A7.

#### If the effective address is specified by the predecrement mode, only a register-to-mem-

#### ory operation is allowed. The registers are stored starting at the specified address

#### minus the operand length (2 or 4), and the address is decremented by the operand

#### length following each transfer. The order of storing is from A7 to A0, then from D7 to

#### D0. When the instruction has completed, the decremented address register contains

#### the address of the last operand stored. For the MC68020, MC68030, MC68040, and

#### CPU32, if the addressing register is also moved to memory, the value written is the ini-

#### tial register value decremented by the size of the operation. The MC68000 and

#### MC68010 write the initial register value (not decremented).

#### If the effective address is specified by the postincrement mode, only a memory-to-reg-

#### ister operation is allowed. The registers are loaded starting at the specified address;

#### the address is incremented by the operand length (2 or 4) following each transfer. The

#### order of loading is the same as that of control mode addressing. When the instruction

#### has completed, the incremented address register contains the address of the last oper-

#### and loaded plus the operand length. If the addressing register is also loaded from

#### memory, the memory value is ignored and the register is written with the postincre-

#### mented effective address.


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-129

# MOVEM Move Multiple Registers MOVEM

#### (M68000 Family)

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### dr field—Specifies the direction of the transfer.

#### 0 — Register to memory.

#### 1 — Memory to register.

#### Size field—Specifies the size of the registers being transferred.

#### 0 — Word transfer

#### 1 — Long transfer

#### Effective Address field—Specifies the memory address for the operation. For register-

#### to-memory transfers, only control alterable addressing modes or the

#### predecrement addressing mode can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 dr 0 0 1 SIZE MODEEFFECTIVE ADDRESS REGISTER
REGISTER LIST MASK
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-130 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVEM Move Multiple Registers MOVEM

#### (M68000 Family)

#### For memory-to-register transfers, only control addressing modes or the postincrement

#### addressing mode can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### Register List Mask field—Specifies the registers to be transferred. The low-order bit

#### corresponds to the first register to be transferred; the high-order bit corresponds

#### to the last register to be transferred. Thus, for both control modes and

#### postincrement mode addresses, the mask correspondence is:

#### For the predecrement mode addresses, the mask correspondence is reversed:

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
A7 A6 A5 A4 A3 A2 A1 A0 D7 D6 D5 D4 D3 D2 D1 D0
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
D0 D1 D2 D3 D4 D5 D6 D7 A0 A1 A2 A3 A4 A5 A6 A7
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-131

# MOVEP Move Peripheral Data MOVEP

#### (M68000 Family)

#### Operation: Source → Destination

#### Assembler MOVEP Dx,(d16,Ay)

#### Syntax: MOVEP (d16,Ay),Dx

#### Attributes: Size = (Word, Long)

#### Description: Moves data between a data register and alternate bytes within the address

#### space starting at the location specified and incrementing by two. The high-order byte

#### of the data register is transferred first, and the low-order byte is transferred last. The

#### memory address is specified in the address register indirect plus 16-bit displacement

#### addressing mode. This instruction was originally designed for interfacing 8-bit

#### peripherals on a 16-bit data bus, such as the MC68000 bus. Although supported by the

#### MC68020, MC68030, and MC68040, this instruction is not useful for those processors

#### with an external 32-bit bus.

#### Example: Long transfer to/from an even address.

#### Byte Organization in Register

#### Byte Organization in

#### 16-Bit Memory

#### (Low Address at Top)

```
31 24 23 16 15 8 7 0
HIGH ORDER MID UPPER MID LOWER LOW ORDER
```
```
15 8 7 0
HIGH ORDER
MID UPPER
MID LOWER
LOW ORDER
```

##### Integer Instructions

##### 4-132 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVEP Move Peripheral Data MOVEP

#### (M68000 Family)

#### Byte Organization in 32-Bit Memory

#### or

#### Example:Word transfer to/from (odd address).

#### Byte Organization in Register

#### Byte Organization in

#### 16-Bit Memory

#### (Low Address at Top)

#### Byte Organization in 32-Bit Memory

#### or

```
31 24 23 16 15 8 7 0
HIGH ORDER MID UPPER
MID LOWER LOW ORDER
```
```
31 24 23 16 15 8 7 0
HIGH ORDER
MID UPPER MID LOWER
LOW ORDER
```
```
31 24 23 16 15 8 7 0
HIGH ORDER LOW ORDER
```
```
15 8 7 0
HIGH ORDER
LOW ORDER
```
```
31 24 23 16 15 8 7 0
HIGH ORDER
LOW ORDER
```
```
31 24 23 16 15 8 7 0
HIGH ORDER LOW ORDER
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-133

# MOVEP Move Peripheral Data MOVEP

#### (M68000 Family)

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Data Register field—Specifies the data register for the instruction.

#### Opmode field—Specifies the direction and size of the operation.

#### 100— Transfer word from memory to register.

#### 101— Transfer long from memory to register.

#### 110— Transfer word from register to memory.

#### 111— Transfer long from register to memory.

#### Address Register field—Specifies the address register which is used in the address

#### register indirect plus displacement addressing mode.

#### Displacement field—Specifies the displacement used in the operand address.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 DATA REGISTER OPMODE 0 0 1 ADDRESS REGISTER
16-BIT DISPLACEMENT
```

##### Integer Instructions

##### 4-134 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVEQ Move Quick MOVEQ

#### (M68000 Family)

#### Operation: Immediate Data → Destination

#### Assembler

#### Syntax: MOVEQ # < data > ,Dn

#### Attributes: Size = (Long)

#### Description: Moves a byte of immediate data to a 32-bit data register. The data in an 8-bit

#### field within the operation word is sign- extended to a long operand in the data register

#### as it is transferred.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies the data register to be loaded.

#### Data field—Eight bits of data, which are sign-extended to a long operand.

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0111 REGISTER 0 DATA
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-135

# MULS Signed Multiply MULS

#### (M68000 Family)

#### Operation: Source x Destination → Destination

#### Assembler MULS.W < ea > ,Dn16 x 16 → 32

#### Syntax: *MULS.L < ea > ,Dl 32 x 32 → 32

#### *MULS.L < ea > ,Dh – Dl 32 x 32 → 64

##### *Applies to MC68020, MC68030, MC68040, CPU32

#### Attributes: Size = (Word, Long)

#### Description: Multiplies two signed operands yielding a signed result. This instruction has a

#### word operand form and a long operand form.

#### In the word form, the multiplier and multiplicand are both word operands, and the result

#### is a long-word operand. A register operand is the low-order word; the upper word of the

#### register is ignored. All 32 bits of the product are saved in the destination data register.

#### In the long form, the multiplier and multiplicand are both long- word operands, and the

#### result is either a long word or a quad word. The long-word result is the low-order 32 bits

#### of the quad- word result; the high-order 32 bits of the product are discarded.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if overflow; cleared otherwise.

#### C — Always cleared.

#### NOTE

#### Overflow (V = 1) can occur only when multiplying 32-bit

#### operands to yield a 32-bit result. Overflow occurs if the high-

#### order 32 bits of the quad-word product are not the sign extension

#### of the low- order 32 bits.

###### X N Z V C

###### — ∗∗∗ 0


##### Integer Instructions

##### 4-136 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MULS Signed Multiply MULS

#### (M68000 Family)

#### Instruction Format:

##### WORD

#### Instruction Fields:

#### Register field—Specifies a data register as the destination.

#### Effective Address field—Specifies the source operand. Only data alterable addressing

#### modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1100 REGISTER (^111) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-137

# MULS Signed Multiply MULS

#### (M68000 Family)

#### Instruction Format:

##### LONG

#### Instruction Fields:

#### Effective Address field—Specifies the source operand. Only data addressing modes

#### can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### Register Dl field—Specifies a data register for the destination operand. The 32-bit

#### multiplicand comes from this register, and the low-order 32 bits of the product are

#### loaded into this register.

#### Size field—Selects a 32- or 64-bit product.

#### 0 — 32-bit product to be returned to register Dl.

#### 1 — 64-bit product to be returned to Dh – Dl.

#### Register Dh field—If size is one, specifies the data register into which the high-order

#### 32 bits of the product are loaded. If Dh = Dl and size is one, the results of the

#### operation are undefined. Otherwise, this field is unused.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100110000) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER DI 1 SIZE 0000000 REGISTER Dh

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-138 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MULU Unsigned Multiply MULU

#### (M68000 Family)

#### Operation: Source x Destination → Destination

#### Assembler MULU.W < ea > ,Dn16 x 16 → 32

#### Syntax: *MULU.L < ea > ,Dl 32 x 32 → 32

#### *MULU.L < ea > ,Dh – Dl 32 x 32 → 64

##### *Applies to MC68020, MC68030, MC68040, CPU32 only

#### Attributes: Size = (Word, Long)

#### Description: Multiplies two unsigned operands yielding an unsigned result. This instruction

#### has a word operand form and a long operand form.

#### In the word form, the multiplier and multiplicand are both word operands, and the result

#### is a long-word operand. A register operand is the low-order word; the upper word of the

#### register is ignored. All 32 bits of the product are saved in the destination data register.

#### In the long form, the multiplier and multiplicand are both long- word operands, and the

#### result is either a long word or a quad word. The long-word result is the low-order 32 bits

#### of the quad- word result; the high-order 32 bits of the product are discarded.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if overflow; cleared otherwise.

#### C — Always cleared.

#### NOTE

#### Overflow (V = 1) can occur only when multiplying 32-bit

#### operands to yield a 32-bit result. Overflow occurs if any of the

#### high-order 32 bits of the quad-word product are not equal to

#### zero.

###### X N Z V C

###### — ∗∗∗ 0


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-139

# MULU Unsigned Multiply MULU

#### (M68000 Family)

#### Instruction Format:

##### WORD

#### Instruction Fields:

#### Register field—Specifies a data register as the destination.

#### Effective Address field—Specifies the source operand. Only data addressing modes

#### can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1100 REGISTER (^011) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-140 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MULU Unsigned Multiply MULU

#### (M68000 Family)

#### Instruction Format:

##### LONG

#### Instruction Fields:

#### Effective Address field—Specifies the source operand. Only data addressing modes

#### can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### Register Dl field—Specifies a data register for the destination operand. The 32-bit

#### multiplicand comes from this register, and the low-order 32 bits of the product are

#### loaded into this register.

#### Size field—Selects a 32- or 64-bit product.

#### 0 — 32-bit product to be returned to register Dl.

#### 1 — 64-bit product to be returned to Dh – Dl.

#### Register Dh field—If size is one, specifies the data register into which the high-order

#### 32 bits of the product are loaded. If Dh = Dl and size is one, the results of the

#### operation are undefined. Otherwise, this field is unused.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100110000) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Dl 0 SIZE 0000000 REGISTER Dh

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-141

# NBCD Negate Decimal with Extend NBCD

#### (M68000 Family)

#### Operation: 0 – Destination 10 – X → Destination

#### Assembler

#### Syntax: NBCD < ea >

#### Attributes: Size = (Byte)

#### Description: Subtracts the destination operand and the extend bit from zero. The operation

#### is performed using binary-coded decimal arithmetic. The packed binary-coded decimal

#### result is saved in the destination location. This instruction produces the tens

#### complement of the destination if the extend bit is zero or the nines complement if the

#### extend bit is one. This is a byte operation only.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Undefined.

#### Z — Cleared if the result is nonzero; unchanged otherwise.

#### V — Undefined.

#### C — Set if a decimal borrow occurs; cleared otherwise.

#### NOTE

#### Normally the Z condition code bit is set via programming before

#### the start of the operation. This allows successful tests for zero

#### results upon completion of multiple-precision operations.

###### X N Z V C

###### ∗ U ∗ U ∗


##### Integer Instructions

##### 4-142 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# NBCD Negate Decimal with Extend NBCD

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100100000) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-143

# NEG Negate NEG

#### (M68000 Family)

#### Operation: 0 – Destination → Destination

#### Assembler

#### Syntax: NEG < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the destination operand from zero and stores the result in the

#### destination location. The size of the operation is specified as byte, word, or long.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Cleared if the result is zero; set otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
01000100 SIZE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### 4-144 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# NEG Negate NEG

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-145

# NEGX Negate with Extend NEGX

#### (M68000 Family)

#### Operation: 0 – Destination – X → Destination

#### Assembler

#### Syntax: NEGX < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the destination operand and the extend bit from zero. Stores the

#### result in the destination location. The size of the operation is specified as byte, word,

#### or long.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Cleared if the result is nonzero; unchanged otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a borrow occurs; cleared otherwise.

#### NOTE

#### Normally the Z condition code bit is set via programming before

#### the start of the operation. This allows successful tests for zero

#### results upon completion of multiple-precision operations.

###### X N Z V C

###### ∗∗∗∗∗


##### Integer Instructions

##### 4-146 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# NEGX Negate with Extend NEGX

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
01000000 SIZE MODEEFFECTIVE ADDRESS REGISTER
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-147

# NOP No Operation NOP

#### (M68000 Family)

#### Operation: None

#### Assembler

#### Syntax: NOP

#### Attributes: Unsized

#### Description: Performs no operation. The processor state, other than the program counter,

#### is unaffected. Execution continues with the instruction following the NOP instruction.

#### The NOP instruction does not begin execution until all pending bus cycles have

#### completed. This synchronizes the pipeline and prevents instruction overlap.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 0 0 1
```

##### Integer Instructions

##### 4-148 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# NOT Logical Complement NOT

#### (M68000 Family)

#### Operation: ~ Destination → Destination

#### Assembler

#### Syntax: NOT < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Calculates the ones complement of the destination operand and stores the

#### result in the destination location. The size of the operation is specified as byte, word,

#### or long.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
01000110 SIZE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-149

# NOT Logical Complement NOT

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00— Byte operation

#### 01— Word operation

#### 10— Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-150 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# OR Inclusive-OR Logical OR

#### (M68000 Family)

#### Operation: Source V Destination → Destination

#### Assembler OR < ea > ,Dn

#### Syntax: OR Dn, < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Performs an inclusive-OR operation on the source operand and the

#### destination operand and stores the result in the destination location. The size of the

#### operation is specified as byte, word, or long. The contents of an address register may

#### not be used as an operand.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies any of the eight data registers.

#### Opmode field

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1000 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```
#### Byte Word Long Operation

#### 000 001 010 < ea > V Dn → Dn

#### 100 101 110 Dn V < ea > → < ea >


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-151

# OR Inclusive-OR Logical OR

#### (M68000 Family)

#### Effective Address field—If the location specified is a source operand, only data

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-152 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# OR Inclusive-OR Logical OR

#### (M68000 Family)

#### If the location specified is a destination operand, only memory alterable addressing

#### modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### If the destination is a data register, it must be specified using the

#### destination Dn mode, not the destination < ea > mode.

#### Most assemblers use ORI when the source is immediate data.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-153

# ORI Inclusive-OR ORI

#### (M68000 Family)

#### Operation: Immediate Data V Destination → Destination

#### Assembler

#### Syntax: ORI # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Performs an inclusive-OR operation on the immediate data and the

#### destination operand and stores the result in the destination location. The size of the

#### operation is specified as byte, word, or long. The size of the immediate data matches

#### the operation size.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00000000 SIZE MODEEFFECTIVE ADDRESS REGISTER
16-BIT WORD DATA 8-BIT BYTE DATA
32-BIT LONG DATA
```

##### Integer Instructions

##### 4-154 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ORI Inclusive-OR ORI

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00— Byte operation

#### 01— Word operation

#### 10— Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### Immediate field—Data immediately following the instruction.

#### If size = 00, the data is the low-order byte of the immediate word.

#### If size = 01, the data is the entire immediate word.

#### If size = 10, the data is the next two immediate words.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-155

# ORI ORI

# to CCR Inclusive-OR Immediate to CCR

## to Condition Codes

#### (M68000 Family)

#### Operation: Source V CCR → CCR

#### Assembler

#### Syntax: ORI # < data > ,CCR

#### Attributes: Size = (Byte)

#### Description: Performs an inclusive-OR operation on the immediate operand and the

#### condition codes and stores the result in the condition code register (low-order byte of

#### the status register). All implemented bits of the condition code register are affected.

#### Condition Codes:

#### X — Set if bit 4 of immediate operand is one; unchanged otherwise.

#### N — Set if bit 3 of immediate operand is one; unchanged otherwise.

#### Z — Set if bit 2 of immediate operand is one; unchanged otherwise.

#### V — Set if bit 1 of immediate operand is one; unchanged otherwise.

#### C — Set if bit 0 of immediate operand is one; unchanged otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 0 0 0 0 0 0 1 1 1 1 0 0
00000000 8-BIT BYTE DATA
```

##### Integer Instructions

##### 4-156 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PACK Pack PACK

#### (MC68020, MC68030, MC68040)

#### Operation: Source (Unpacked BCD) + Adjustment → Destination (Packed BCD)

#### Assembler PACK – (Ax), – (Ay),# < adjustment >

#### Syntax: PACK Dx,Dy,# < adjustment >

#### Attributes: Unsized

#### Description: Adjusts and packs the lower four bits of each of two bytes into a single byte.

#### When both operands are data registers, the adjustment is added to the value contained

#### in the source register. Bits 11 – 8 and 3 – 0 of the intermediate result are concatenated

#### and placed in bits 7 – 0 of the destination register. The remainder of the destination

#### register is unaffected.

#### Source:

#### Add Adjustment Word:

#### Resulting in:

#### Destination:

#### When the predecrement addressing mode is specified, two bytes from the source are

#### fetched and concatenated. The adjustment word is added to the concatenated bytes.

#### Bits 3 – 0 of each byte are extracted. These eight bits are concatenated to form a new

#### byte which is then written to the destination.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
xxxxab c d x x x x e f g h
Dx
```
```
15 0
16-BIT EXTENSION
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
x’ x’ x’ x’ a’ b’ c’ d’ x’ x’ x’ x’ e’ f’ g’ h’
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
u u u u u u u u a’ b’ c’ d’ e’ f’ g’ h’
Dy
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-157

# PACK Pack PACK

#### (MC68020, MC68030, MC68040)

#### Source:

#### Concatenated Word:

#### Add Adjustment Word:

#### Destination:

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
7 6 5 4 3 2 1 0
x x x x a b c d
x x x x e f g h
Ax
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
xxxxab c d x x x x e f g h
```
###### 15 0

###### 16-BIT EXTENSION

###### 7 6 5 4 3 2 1 0

```
a’ b’ c’ d’ e’ f’ g’ h’
Ay
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1000 REGISTER Dy/Ay 1 0 1 0 0 R/M REGISTER Dx/Ax
16-BIT ADJUSTMENT EXTENSION:
```

##### Integer Instructions

##### 4-158 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PACK Pack PACK

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Register Dy/Ay field—Specifies the destination register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register in the predecrement addressing mode.

#### R/M field—Specifies the operand addressing mode.

#### 0 — The operation is data register to data register.

#### 1 — The operation is memory to memory.

#### Register Dx/Ax field—Specifies the source register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register in the predecrement addressing mode.

#### Adjustment field—Immediate data word that is added to the source operand. This word

#### is zero to pack ASCII or EBCDIC codes. Other values can be used for other

#### codes.


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-159

# PEA Push Effective Address PEA

#### (M68000 Family)

#### Operation: SP – 4 → SP; < ea > → (SP)

#### Assembler

#### Syntax: PEA < ea >

#### Attributes: Size = (Long)

#### Description: Computes the effective address and pushes it onto the stack. The effective

#### address is a long address.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Field:

#### Effective Address field—Specifies the address to be pushed onto the stack. Only

#### control addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100100001) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + — —
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-160 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ROL, ROR Rotate (Without Extend) ROL, ROR

#### (M68000 Family)

#### Operation: Destination Rotated By < count > → Destination

#### Assembler ROd Dx,Dy

#### Syntax: ROd # < data > ,Dy ROd < ea > where d is direction, L or R

#### Attributes: Size = (Byte, Word, Long)

#### Description: Rotates the bits of the operand in the direction specified (L or R). The extend

#### bit is not included in the rotation. The rotate count for the rotation of a register is

#### specified in either of two ways:

#### 1. Immediate—The rotate count (1 – 8) is specified in the instruction.

#### 2. Register—The rotate count is the value in the data register specified in the in-

#### struction, modulo 64.

#### The size of the operation for register destinations is specified as byte, word, or long.

#### The contents of memory, (ROd < ea > ), can be rotated one bit only, and operand size

#### is restricted to a word.

#### The ROL instruction rotates the bits of the operand to the left; the rotate count deter-

#### mines the number of bit positions rotated. Bits rotated out of the high-order bit go to the

#### carry bit and also back into the low-order bit.

#### .

#### The ROR instruction rotates the bits of the operand to the right; the rotate count deter-

#### mines the number of bit positions rotated. Bits rotated out of the low-order bit go to the

#### carry bit and also back into the high-order bit.

#### .

```
C OPERAND
```
```
ROL:
```
```
OPERAND C
```
```
ROR:
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-161

# ROL,ROR Rotate (Without Extend) ROL,ROR

#### (M68000 Family)

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Set according to the last bit rotated out of the operand; cleared when the rotate

#### count is zero.

#### Instruction Format:

##### REGISTER ROTATE

#### Instruction Fields:

#### Count/Register field:

#### If i/r = 0, this field contains the rotate count. The values 1 – 7 represent counts of 1

- 7, and zero specifies a count of eight.

#### If i/r = 1, this field specifies a data register that contains the rotate count (modulo 64).

#### dr field—Specifies the direction of the rotate.

#### 0 — Rotate right

#### 1 — Rotate left

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### i/r field—Specifies the rotate count location.

#### If i/r = 0, immediate rotate count.

#### If i/r = 1, register rotate count.

#### Register field—Specifies a data register to be rotated.

###### X N Z V C

###### — ∗∗ 0 ∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110) REGISTERCOUNT/ dr SIZE i/r 1 1 REGISTER


##### Integer Instructions

##### 4-162 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ROL, ROR Rotate (Without Extend) ROL, ROR

#### (M68000 Family)

#### Instruction Format:

##### MEMORY ROTATE

#### Instruction Fields:

#### dr field—Specifies the direction of the rotate.

#### 0 — Rotate right

#### 1 — Rotate left

#### Effective Address field—Specifies the operand to be rotated. Only memory alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1 1 1 0 0 1 1 dr (^11) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-163

# ROXL, ROXR Rotate with Extend ROXL, ROXR

#### (M68000 Family)

#### Operation: Destination Rotated With X By Count → Destination

#### Assembler ROXd Dx,Dy

#### Syntax: ROXd # < data > ,Dy

#### ROXd < ea >

#### where d is direction, L or R

#### Attributes: Size = (Byte, Word, Long)

#### Description: Rotates the bits of the operand in the direction specified (L or R). The extend

#### bit is included in the rotation. The rotate count for the rotation of a register is specified

#### in either of two ways:

#### 1. Immediate—The rotate count (1 – 8) is specified in the instruction.

#### 2. Register—The rotate count is the value in the data register specified in the in-

#### struction, modulo 64.

#### The size of the operation for register destinations is specified as byte, word, or long.

#### The contents of memory, < ea > , can be rotated one bit only, and operand size is

#### restricted to a word. The ROXL instruction rotates the bits of the operand to the left; the

#### rotate count determines the number of bit positions rotated. Bits rotated out of the high-

#### order bit go to the carry bit and the extend bit; the previous value of the extend bit

#### rotates into the low-order bit.

#### .

#### The ROXR instruction rotates the bits of the operand to the right; the rotate count deter-

#### mines the number of bit positions rotated. Bits rotated out of the low-order bit go to the

#### carry bit and the extend bit; the previous value of the extend bit rotates into the high-

#### order bit.

#### .

```
ROXL: C OPERAND X
```
```
ROXR: X OPERAND C
```

##### Integer Instructions

##### 4-164 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# ROXL, ROXR Rotate with Extend ROXL, ROXR

#### (M68000 Family)

#### Condition Codes:

#### X — Set to the value of the last bit rotated out of the operand; unaffected when the

#### rotate count is zero.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Set according to the last bit rotated out of the operand; when the rotate count is

#### zero, set to the value of the extend bit.

#### Instruction Format:

##### REGISTER ROTATE

#### Instruction Fields:

#### Count/Register field:

#### If i/r = 0, this field contains the rotate count. The values 1 – 7 represent counts of 1

- 7, and zero specifies a count of eight.

#### If i/r = 1, this field specifies a data register that contains the rotate count (modulo 64).

#### dr field—Specifies the direction of the rotate.

#### 0 — Rotate right

#### 1 — Rotate left

###### X N Z V C

###### ∗∗∗ 0 ∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1110) REGISTERCOUNT/ dr SIZE i/r 1 0 REGISTER


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-165

# ROXL, ROXR Rotate with Extend ROXL, ROXR

#### (M68000 Family)

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### i/r field—Specifies the rotate count location.

#### If i/r = 0, immediate rotate count.

#### If i/r = 1, register rotate count.

#### Register field—Specifies a data register to be rotated.

#### Instruction Format:

##### MEMORY ROTATE

#### Instruction Fields:

#### dr field—Specifies the direction of the rotate.

#### 0 — Rotate right

#### 1 — Rotate left

#### Effective Address field—Specifies the operand to be rotated. Only memory alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1 1 1 0 0 1 0 dr (^11) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-166 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# RTD Return and Deallocate RTD

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### Operation: (SP) → PC; SP + 4 + dn → SP

#### Assembler

#### Syntax: RTD # < displacement >

#### Attributes: Unsized

#### Description: Pulls the program counter value from the stack and adds the sign-extended

#### 16-bit displacement value to the stack pointer. The previous program counter value is

#### lost.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Field:

#### Displacement field—Specifies the twos complement integer to be sign-extended and

#### added to the stack pointer.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 1 0 0
16-BIT DISPLACEMENT
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-167

# RTM Return from Module RTM

#### (MC68020)

#### Operation: Reload Saved Module State from Stack

#### Assembler

#### Syntax: RTM Rn

#### Attributes: Unsized

#### Description: A previously saved module state is reloaded from the top of stack. After the

#### module state is retrieved from the top of the stack, the caller’s stack pointer is

#### incremented by the argument count value in the module state.

#### Condition Codes:

#### Set according to the content of the word on the stack.

#### Instruction Format:

#### Instruction Fields:

#### D/A field—Specifies whether the module data pointer is in a data or an address register.

#### 0 — the register is a data register

#### 1 — the register is an address register

#### Register field—Specifies the register number for the module data area pointer to be

#### restored from the saved module state. If the register specified is A7 (SP), the

#### updated value of the register reflects the stack pointer operations, and the saved

#### module data area pointer is lost.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 0 1 1 0 1 1 0 0 D/A REGISTER
```

##### Integer Instructions

##### 4-168 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# RTR Return and Restore Condition Codes RTR

#### (M68000 Family)

#### Operation: (SP) → CCR; SP + 2 → SP; (SP) → PC; SP + 4 → SP

#### Assembler

#### Syntax: RTR

#### Attributes: Unsized

#### Description: Pulls the condition code and program counter values from the stack. The

#### previous condition code and program counter values are lost. The supervisor portion

#### of the status register is unaffected.

#### Condition Codes:

#### Set to the condition codes from the stack.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 1 1 1
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-169

# RTS Return from Subroutine RTS

#### (M68000 Family)

#### Operation: (SP) → PC; SP + 4 → SP

#### Assembler

#### Syntax: RTS

#### Attributes: Unsized

#### Description: Pulls the program counter value from the stack. The previous program counter

#### value is lost.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 1 0 1
```

##### Integer Instructions

##### 4-170 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# SBCD Subtract Decimal with Extend SBCD

#### (M68000 Family)

#### Operation: Destination10 – Source10 – X → Destination

#### Assembler SBCD Dx,Dy

#### Syntax: SBCD – (Ax), – (Ay)

#### Attributes: Size = (Byte)

#### Description: Subtracts the source operand and the extend bit from the destination operand

#### and stores the result in the destination location. The subtraction is performed using

#### binary-coded decimal arithmetic; the operands are packed binary-coded decimal

#### numbers. The instruction has two modes:

#### 1. Data register to data register—the data registers specified in the instruction con-

#### tain the operands.

#### 2. Memory to memory—the address registers specified in the instruction access

#### the operands from memory using the predecrement addressing mode.

#### This operation is a byte operation only.

#### Condition Codes:

#### X — Set the same as the carry bit.

#### N — Undefined.

#### Z — Cleared if the result is nonzero; unchanged otherwise.

#### V — Undefined.

#### C — Set if a borrow (decimal) is generated; cleared otherwise.

#### NOTE

#### Normally the Z condition code bit is set via programming before

#### the start of an operation. This allows successful tests for zero

#### results upon completion of multiple-precision operations.

###### X N Z V C

###### ∗ U ∗ U ∗


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-171

# SBCD Subtract Decimal with Extend SBCD

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Register Dy/Ay field—Specifies the destination register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

#### R/M field—Specifies the operand addressing mode.

#### 0 — The operation is data register to data register.

#### 1 — The operation is memory to memory.

#### Register Dx/Ax field—Specifies the source register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1000 REGISTER Dy/Ay 1 0 0 0 0 R/M REGISTER Dx/Ax
```

##### Integer Instructions

##### 4-172 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# Scc Set According to Condition Scc

#### (M68000 Family)

#### Operation: If Condition True

#### Then 1s → Destination

#### Else 0s → Destination

#### Assembler

#### Syntax: Scc < ea >

#### Attributes: Size = (Byte)

#### Description: Tests the specified condition code; if the condition is true, sets the byte

#### specified by the effective address to TRUE (all ones). Otherwise, sets that byte to

#### FALSE (all zeros). Condition code cc specifies one of the following conditional tests

#### (refer to Table 3-19 for more information on these conditional tests):

#### Condition Codes:

#### Not affected.

##### Mnemonic Condition Mnemonic Condition

```
CC(HI) Carry Clear LS Low or Same
CS(LO) Carry Set LT Less Than
EQ Equal MI Minus
F False NE Not Equal
GE Greater or Equal PL Plus
GT Greater Than T True
HI High VC Overflow Clear
LE Less or Equal VS Overflow Set
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-173

# Scc Set According to Condition Scc

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Condition field—The binary code for one of the conditions listed in the table.

#### Effective Address field—Specifies the location in which the TRUE/FALSE byte is to be

#### stored. Only data alterable addressing modes can be used as listed in the

#### following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### A subsequent NEG.B instruction with the same effective

#### address can be used to change the Scc result from TRUE or

#### FALSE to the equivalent arithmetic value (TRUE = 1, FALSE =

#### 0). In the MC68000 and MC68008, a memory destination is read

#### before it is written.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
0101 CONDITION (^11) MODEEFFECTIVE ADDRESS REGISTER

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-174 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# SUB Subtract SUB

#### (M68000 Family)

#### Operation: Destination – Source → Destination

#### Assembler SUB < ea > ,Dn

#### Syntax: SUB Dn, < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the source operand from the destination operand and stores the

#### result in the destination. The size of the operation is specified as byte, word, or long.

#### The mode of the instruction indicates which operand is the source, which is the

#### destination, and which is the operand size.

#### Condition Codes:

#### X — Set to the value of the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow is generated; cleared otherwise.

#### C — Set if a borrow is generated; cleared otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1001 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-175

# SUB Subtract SUB

#### (M68000 Family)

#### Instruction Fields:

#### Register field—Specifies any of the eight data registers.

#### Opmode field

#### Effective Address field—Determines the addressing mode. If the location specified is a

#### source operand, all addressing modes can be used as listed in the following

#### tables:

```
*For byte-sized operation, address register direct is not allowed.
**Can be used with CPU32.
```
#### Byte Word Long Operation

#### 000 001 010 Dn – < ea > → Dn

#### 100 101 110 < ea > – Dn → < ea >

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)** 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-176 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# SUB Subtract SUB

#### (M68000 Family)

#### If the location specified is a destination operand, only memory alterable addressing

#### modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### NOTE

#### If the destination is a data register, it must be specified as a

#### destination Dn address, not as a destination < ea > address.

#### Most assemblers use SUBA when the destination is an address

#### register and SUBI or SUBQ when the source is immediate data.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-177

# SUBA Subtract Address SUBA

#### (M68000 Family)

#### Operation: Destination – Source → Destination

#### Assembler

#### Syntax: SUBA < ea > ,An

#### Attributes: Size = (Word, Long)

#### Description: Subtracts the source operand from the destination address register and stores

#### the result in the address register. The size of the operation is specified as word or long.

#### Word-sized source operands are sign-extended to 32-bit quantities prior to the

#### subtraction.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies the destination, any of the eight address registers.

#### Opmode field—Specifies the size of the operation.

#### 011— Word operation. The source operand is sign-extended to a long operand and

#### the operation is performed on the address register using all 32 bits.

#### 111— Long operation.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1001 REGISTER OPMODE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### 4-178 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# SUBA Subtract Address SUBA

#### (M68000 Family)

#### Effective Address field—Specifies the source operand. All addressing modes can be

#### used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-179

# SUBI Subtract Immediate SUBI

#### (M68000 Family)

#### Operation: Destination – Immediate Data → Destination

#### Assembler

#### Syntax: SUBI # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the immediate data from the destination operand and stores the

#### result in the destination location. The size of the operation is specified as byte, word,

#### or long. The size of the immediate data matches the operation size.

#### Condition Codes:

#### X — Set to the value of the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a borrow occurs; cleared otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00000100 SIZE MODEEFFECTIVE ADDRESS REGISTER
16-BIT WORD DATA 8-BIT BYTE DATA
32-BIT LONG DATA
```

##### Integer Instructions

##### 4-180 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# SUBI Subtract Immediate SUBI

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the destination operand. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
#### Immediate field—Data immediately following the instruction.

#### If size = 00, the data is the low-order byte of the immediate word.

#### If size = 01, the data is the entire immediate word.

#### If size = 10, the data is the next two immediate words.

##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-181

# SUBQ Subtract Quick SUBQ

#### (M68000 Family)

#### Operation: Destination – Immediate Data → Destination

#### Assembler

#### Syntax: SUBQ # < data > , < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the immediate data (1 – 8) from the destination operand. The size

#### of the operation is specified as byte, word, or long. Only word and long operations can

#### be used with address registers, and the condition codes are not affected. When

#### subtracting from address registers, the entire destination address register is used,

#### despite the operation size.

#### Condition Codes:

#### X — Set to the value of the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a borrow occurs; cleared otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 1 DATA 1 SIZE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### 4-182 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# SUBQ Subtract Quick SUBQ

#### (M68000 Family)

#### Instruction Fields:

#### Data field—Three bits of immediate data; 1 – 7 represent immediate values of 1 – 7,

#### and zero represents eight.

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the destination location. Only alterable addressing

#### modes can be used as listed in the following tables:

```
*Word and long only.
**Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)** 110 reg. number:An (bd,PC,Xn)** — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-183

# SUBX Subtract with Extend SUBX

#### (M68000 Family)

#### Operation: Destination – Source – X → Destination

#### Assembler SUBX Dx,Dy

#### Syntax: SUBX – (Ax), – (Ay)

#### Attributes: Size = (Byte, Word, Long)

#### Description: Subtracts the source operand and the extend bit from the destination operand

#### and stores the result in the destination

#### location. The instruction has two modes:

#### 1. Data register to data register—the data registers specified in the instruction con-

#### tain the operands.

#### 2. Memory to memory—the address registers specified in the instruction access

#### the operands from memory using the predecrement addressing mode.

#### The size of the operand is specified as byte, word, or long.

#### Condition Codes:

#### X — Set to the value of the carry bit.

#### N — Set if the result is negative; cleared otherwise.

#### Z — Cleared if the result is nonzero; unchanged otherwise.

#### V — Set if an overflow occurs; cleared otherwise.

#### C — Set if a borrow occurs; cleared otherwise.

#### NOTE

#### Normally the Z condition code bit is set via programming before

#### the start of an operation. This allows successful tests for zero

#### results upon completion of multiple-precision operations.

###### X N Z V C

###### ∗∗∗∗∗


##### Integer Instructions

##### 4-184 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# SUBX Subtract with Extend SUBX

#### (M68000 Family)

#### Instruction Format:

#### Instruction Fields:

#### Register Dy/Ay field—Specifies the destination register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### R/M field—Specifies the operand addressing mode.

#### 0 — The operation is data register to data register.

#### 1 — The operation is memory to memory.

#### Register Dx/Ax field—Specifies the source register:

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register for the predecrement addressing mode.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1001 REGISTER Dy/Ay 1 SIZE 0 0 R/M REGISTER Dx/Ax
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-185

# SWAP Swap Register Halves SWAP

#### (M68000 Family)

#### Operation: Register 31 – 16 ←→ Register 15 – 0

#### Assembler

#### Syntax: SWAP Dn

#### Attributes: Size = (Word)

#### Description: Exchange the 16-bit words (halves) of a data register.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the 32-bit result is set; cleared otherwise.

#### Z — Set if the 32-bit result is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

#### Instruction Field:

#### Register field—Specifies the data register to swap.

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0100100001000 REGISTER
```

##### Integer Instructions

##### 4-186 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# TAS Test and Set an Operand TAS

#### (M68000 Family)

#### Operation: Destination Tested → Condition Codes; 1 → Bit 7 of Destination

#### Assembler

#### Syntax: TAS < ea >

#### Attributes: Size = (Byte)

#### Description: Tests and sets the byte operand addressed by the effective address field. The

#### instruction tests the current value of the operand and sets the N and Z condition bits

#### appropriately. TAS also sets the high-order bit of the operand. The operation uses a

#### locked or read-modify-write transfer sequence. This instruction supports use of a flag

#### or semaphore to coordinate several processors.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the operand is currently set; cleared otherwise.

#### Z — Set if the operand was zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100101011) MODEEFFECTIVE ADDRESS REGISTER


##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-187

# TAS Test and Set an Operand TAS

#### (M68000 Family)

#### Instruction Fields:

#### Effective Address field—Specifies the location of the tested operand. Only data

#### alterable addressing modes can be used as listed in the following tables:

```
*Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An #<data> — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —
```

##### Integer Instructions

##### 4-188 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# TRAP Trap TRAP

#### (M68000 Family)

#### Operation: 1 → S-Bit of SR

#### *SSP – 2 → SSP; Format/Offset → (SSP);

#### SSP – 4 → SSP; PC → (SSP); SSP – 2 → SSP;

#### SR → (SSP); Vector Address → PC

##### *The MC68000 and MC68008 do not write vector offset or

##### format code to the system stack.

#### Assembler

#### Syntax: TRAP # < vector >

#### Attributes: Unsized

#### Description: Causes a TRAP # < vector > exception. The instruction adds the immediate

#### operand (vector) of the instruction to 32 to obtain the vector number. The range of

#### vector values is 0 – 15, which provides 16 vectors.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Vector field—Specifies the trap vector to be taken.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
010011100100 VECTOR
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-189

# TRAPcc Trap on Condition TRAPcc

#### (MC68020, MC68030, MC68040, CPU32)

#### Operation: If cc

#### Then TRAP

#### Assembler TRAPcc

#### Syntax: TRAPcc.W # < data >

#### TRAPcc.L # < data >

#### Attributes: Unsized or Size = (Word, Long)

#### Description: If the specified condition is true, causes a TRAPcc exception with a vector

#### number 7. The processor pushes the address of the next instruction word (currently in

#### the program counter) onto the stack. If the condition is not true, the processor performs

#### no operation, and execution continues with the next instruction. The immediate data

#### operand should be placed in the next word(s) following the operation word and is

#### available to the trap handler. Condition code cc specifies one of the following

#### conditional tests (refer to Table 3-19 for more information on these conditional tests):

#### Condition Codes:

#### Not affected.

##### Mnemonic Condition Mnemonic Condition

```
CC(HI) Carry Clear LS Low or Same
CS(LO) Carry Set LT Less Than
EQ Equal MI Minus
F False NE Not Equal
GE Greater or Equal PL Plus
GT Greater Than T True
HI High VC Overflow Clear
LE Less or Equal VS Overflow Set
```

##### Integer Instructions

##### 4-190 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# TRAPcc Trap on Condition TRAPcc

#### (MC68020, MC68030, MC68040, CPU32)

#### Instruction Format:

#### Instruction Fields:

#### Condition field—The binary code for one of the conditions listed in the table.

#### Opmode field—Selects the instruction form.

#### 010— Instruction is followed by word-sized operand.

#### 011— Instruction is followed by long-word-sized operand.

#### 100— Instruction has no operand.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0101 CONDITION 11111 OPMODE
OPTIONAL WORD
OR LONG WORD
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-191

# TRAPV Trap on Overflow TRAPV

#### (M68000 Family)

#### Operation: If V

#### Then TRAP

#### Assembler

#### Syntax: TRAPV

#### Attributes: Unsized

#### Description: If the overflow condition is set, causes a TRAPV exception with a vector

#### number 7. If the overflow condition is not set, the processor performs no operation and

#### execution continues with the next instruction.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 1 1 0
```

##### Integer Instructions

##### 4-192 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# TST Test an Operand TST

#### (M68000 Family)

#### Operation: Destination Tested → Condition Codes

#### Assembler

#### Syntax: TST < ea >

#### Attributes: Size = (Byte, Word, Long)

#### Description: Compares the operand with zero and sets the condition codes according to

#### the results of the test. The size of the operation is specified as byte, word, or long.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the operand is negative; cleared otherwise.

#### Z — Set if the operand is zero; cleared otherwise.

#### V — Always cleared.

#### C — Always cleared.

#### Instruction Format:

###### X N Z V C

###### — ∗∗ 0 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
01001010 SIZE MODEEFFECTIVE ADDRESS REGISTER
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-193

# TST Test an Operand TST

#### (M68000 Family)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00 — Byte operation

#### 01 — Word operation

#### 10 — Long operation

#### Effective Address field—Specifies the addressing mode for the destination operand as

#### listed in the following tables:

```
*MC68020, MC68030, MC68040, and CPU32. Address register direct allowed only for word
and long.
**PC relative addressing modes do not apply to MC68000, MC680008, or MC68010.
***Can be used with CPU32.
```
##### Addressing Mode Mode Register Addressing Mode Mode Register

```
Dn 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An #<data>* 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC)** 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn)** 111 011

##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)*** 110 reg. number:An (bd,PC,Xn)*** 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Integer Instructions

##### 4-194 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# UNLK Unlink UNLK

#### (M68000 Family)

#### Operation: An → SP; (SP) → An; SP + 4 → SP

#### Assembler

#### Syntax: UNLK An

#### Attributes: Unsized

#### Description: Loads the stack pointer from the specified address register, then loads the

#### address register with the long word pulled from the top of the stack.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Field:

#### Register field—Specifies the address register for the instruction.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0100111001011 REGISTER
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-195

# UNPK Unpack BCD UNPK

#### (MC68020, MC68030, MC68040)

#### Operation: Source (Packed BCD) + Adjustment → Destination (Unpacked BCD)

#### Assembler UNPACK – (Ax), – (Ay),# < adjustment >

#### Syntax: UNPK Dx,Dy,# < adjustment >

#### Attributes: Unsized

#### Description: Places the two binary-coded decimal digits in the source operand byte into the

#### lower four bits of two bytes and places zero bits in the upper four bits of both bytes.

#### Adds the adjustment value to this unpacked value. Condition codes are not altered.

#### When both operands are data registers, the instruction unpacks the source register

#### contents, adds the extension word, and places the result in the destination register.

#### The high word of the destination register is unaffected.

#### Source:

#### Intermediate Expansion:

#### Add Adjustment Word:

#### Destination:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
u u u u u u u u a b c d e f g h
Dx
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 a b c d 0 0 0 0 e f g h
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
16-BIT EXTENSION
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
v v v v a’ b’ c’ d’ w w w w e’ f’ g’ h’
Dy
```

##### Integer Instructions

##### 4-196 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# UNPK Unpack BCD UNPK

#### (MC68020, MC68030, MC68040)

#### When the specified addressing mode is predecrement, the instruction extracts two

#### binary-coded decimal digits from a byte at the source address. After unpacking the dig-

#### its and adding the adjustment word, the instruction writes the two bytes to the destina-

#### tion address. Source:

#### Intermediate Expansion:

#### Add Adjustment Word:

#### Destination:

#### Condition Codes:

#### Not affected.

#### Instruction Format:

###### 7 6 5 4 3 2 1 0

```
a b c d e f g h
Ax
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 a b c d 0 0 0 0 e f g h
```
```
15 0
16-BIT EXTENSION
```
###### 7 6 5 4 3 2 1 0

```
v v v v a’ b’ c’ d’
w w w w e’ f’ g’ h’
Ay
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1000 REGISTER Dy/Ay 1 1 0 0 0 R/M REGISTER Dx/Ax
16-BIT EXTENSION: ADJUSTMENT
```

##### Integer Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 4-197

# UNPK Unpack BCD UNPK

#### (MC68020, MC68030, MC68040)

#### Instruction Fields:

#### Register Dy/Ay field—Specifies the destination register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register in the predecrement addressing mode.

#### R/M field—Specifies the operand addressing mode.

#### 0 — The operation is data register to data register.

#### 1 — The operation is memory to memory.

#### Register Dx/Ax field—Specifies the data register.

#### If R/M = 0, specifies a data register.

#### If R/M = 1, specifies an address register in the predecrement addressing mode.

#### Adjustment field—Immediate data word that is added to the source operand.

#### Appropriate constants can be used as the adjustment to translate from binary-

#### coded decimal to the desired code. The constant used for ASCII is $3030; for

#### EBCDIC, $F0F0.


##### Integer Instructions

##### 4-198 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA


##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 5-1

## SECTION 5

## FLOATING POINT INSTRUCTIONS

#### This section contains information about the floating-point instructions for the MC68881,

#### MC68882, and MC68040. In this section, all references to the MC68040 do not include the

#### MC68LC040 and MC68EC040. Each instruction is described in detail, and the instruction

#### descriptions are arranged in alphabetical order by instruction mnemonic.

#### All floating-point instructions apply to the MC68881 and MC68882 processors. The

#### MC68040 directly supports part of the floating-point instructions through hardware. It

#### indirectly supports the remainder by providing special traps and/or stack frames for the

#### unimplemented instructions and data types. The following identification is noted under the

#### instruction title for the MC68040:

#### Directly Supported—(MC6888X, MC68040)

#### Software Supported—(MC6888X, MC68040FPSW)

#### For all MC68040 floating-point instructions, the coprocessor ID field must be 001.

#### Table 5-1 lists the floating-point instructions directly supported by the MC68040, and Table

#### 5-2 lists the floating-point instructions indirectly supported.


##### Floating Point Instructions

##### 5-2

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

```
*These are privileged instructions; refer to
Section 6 Supervisor (Privaleged) Instructions
for
detailed information.
```
#### Table 5-1. Directly Supported Floating-Point Instructions

```
Mnemonic Description
FABS Floating-Point Absolute Value
FADD Floating-Point Add
FBcc Floating-Point Branch Conditionally
FCMP Floating-Point Compare
FDBcc Floating-Point Test Condition, Decrement, and Branch
FDIV Floating-Point Divide
FMOVE Move Floating-Point Data Register
FMOVE Move Floating-Point System Control Register
FMOVEM Move Multiple Floating-Point System Data Register
FMOVEM Move Multiple Floating-Point Control Data Register
FMUL Floating-Point Multiply
FNEG Floating-Point Negate
FNOP No Operation
FRESTORE* Restore Internal Floating-Point State*
FSAVE* Save Internal Floating-Point State*
FScc Set According to Floating-Point Condition
FSORT Floating-Point Square Root
FSUB Floating-Point Subtract
FSGLDIV Floating-Point Single-Precision Divide
FSFLMUL Floating-Point Single-Precision Multiply
FTRAPcc Trap on Floating-Point Condition
FTST Test Floating-Point Operand
```

##### Floating Point Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 5-3

#### Table 5-2. Indirectly Supported Floating-Point Instructions

```
Mnemonic Description
FACOS Floating-Point Arc Cosine
FASIN Floating-Point Arc Sine
FATAN Floating-Point Arc Tangent
FATANH Floating-Point Hyperbolic Arc Tangent
FCOS Floating-Point Cosine
FCOSH Floating-Point Hyperbolic Cosine
FETOX Floating-Point e
x
FETOXM1 Floating-Point e
x
```
- 1
FGETEXP Floating-Point Get Exponent
FGETMAN Floating-Point Get Mantissa
FINT Floating-Point Integer Part
FINTRZ Floating-Point Integer Part, Round-to- Zero
FLOG10 Floating-Point Log10
FLOG2 Floating-Point Log2
FLOGN Floating-Point Loge
FLOGNP1 Floating-Point Log
e (x + 1)
FMOD Floating-Point Modulo Remainder
FMOVECR Floating-Point Move Constant ROM
FREM Floating-Point IEEE Remainder
FSCALE Floating-Point Scale Exponent
FSIN Floating-Point Sine
FSINCOS Floating-Point Simultaneous Sine and Cosine
FSINH Floating-Point Hyperbolic Sine
FTAN Floating-Point Tangent
FTANH Floating-Point Hyperbolic Tangent
FTENTOX Floating-Point 10
x
FTWOTOX Floating-Point 2
x


##### Floating Point Instructions

##### 5-4

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# FABS

## Floating-Point Absolute Value

# FABS

#### (MC6888X, MC68040)

#### Operation:

#### Absolute Value of Source

#### →

#### FPn

#### Assembler

#### Syntax:

#### FABS. < fmt > < ea > ,FPn

#### FABS.X FPm,FPn

#### FABS.X FPn

#### *FrABS. < fmt > < ea > ,FPn

#### *FrABS.X FPm,FPn

#### *FrABS.X Pn

#### where r is rounding precision, S or D

##### *Supported by MC68040 only.

#### Attributes:

#### Format = (Byte, Word, Long, Single, Quad, Extended, Packed)

#### Description:

#### Converts the source operand to extended precision (if necessary) and stores

#### the absolute value of that number in the destination floating-point data register.

#### FABS will round the result to the precision selected in the floating-point control register.

#### FSABS and FDABS will round the result to single or double precision, respectively,

#### regardless of the rounding precision selected in the floating-point control register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to
1.6.5 Not-A-Numbers
for more information
```
##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result
Absolute Value Absolute Value Absolute Value
```

##### Floating Point Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 5-5

# FABS

## Floating-Point Absolute Value

# FABS

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in

#### 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to

#### 1.6.5 Not-A-Numbers

#### OPERR Cleared

#### OVFL Cleared

#### UNFL If the source is an extended-precision

#### denormalized number, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing; refer to the

#### appropriate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE


##### Floating Point Instructions

##### 5-6

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# FABS

## Floating-Point Absolute Value

# FABS

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field specifies the location of the source operand. Only data

#### addressing modes can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d
16
,An) 101 reg. number:An (d
16

###### ,PC) 111 010

```
(d
8
,An,Xn) 110 reg. number:An (d
8
,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Floating Point Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 5-7

# FABS

## Floating-Point Absolute Value

# FABS

#### (MC6888X, MC68040)

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding will cause an unimplemented

##### data type exception in the MC68040 to allow emulation in software.

#### Destination Register field—Specifies the destination floating- point data register.

#### Opmode field—Specifies the instruction and rounding precision.

#### 0011000 FABS Rounding precision specified by the floating-point controlregister.

#### 1011000 FSABS Single-precision rounding specified.

#### 1011100 FDABS Double-precision rounding specified.


##### Floating Point Instructions

##### 5-8

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# FACOS

## Arc Cosine

# FACOS

#### (MC6888X, M68040FPSP)

#### Operation:

#### Arc Cosine of Source

#### →

#### FPn

#### Assembler

#### FACOS. < fmt > < ea > ,FPn

#### Syntax:

#### FACOS.X FPm,FPn

#### FACOS.X FPn

#### Attributes:

#### Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description:

#### Converts the source operand to extended precision (if necessary) and

#### calculates the arc cosine of that number. Stores the result in the destination floating-

#### point data register. This function is not defined for source operands outside of the range

#### [ – 1... + 1]; if the source is not in the correct range, a NAN is returned as the result and

#### the OPERR bit is set in the floating- point status register. If the source is in the correct

#### range, the result is in the range of [0...

#### π

#### ].

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to
    **1.6.5 Not-A-Numbers**
       for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in

#### 3.6.2 Conditional Testing

#### .

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to

#### 1.6.5 Not-A-Numbers

#### .

#### OPERR Set if the source is infinity, > + 1 or < – 1;

#### cleared otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result
Arc Cosine +
π
/2 NAN
```

##### Floating Point Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 5-9

# FACOS

## Arc Cosine

# FACOS

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 1 1 1 0 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d
16
,An) 101 reg. number:An (d
16

###### ,PC) 111 010

```
(d
8
,An,Xn) 110 reg. number:An (d
8
,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011
```

##### Floating Point Instructions

##### 5-10

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# FACOS

## Arc Cosine

# FACOS

#### (MC6888X, M68040FPSP)

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is then written

#### into the same register. If the single register syntax is used, Motorola assemblers

#### set the source and destination fields to the same value.


##### Floating Point Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 5-11

# FADD

## Floating-Point Add

# FADD

#### (MC6888X, MC68040)

#### Operation:

#### Source + FPn

#### →

#### FPn

#### Assembler FADD. < fmt > < ea > ,FPn

#### Syntax: FADD.X FPm,FPn

#### *FrADD. < fmt > < ea > ,FPn

#### *FrADD.X FPm,FPn

#### where r is rounding precision, S or D

##### *Supported by MC68040 only.

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and adds

#### that number to the number contained in the destination floating-point data register.

#### Stores the result in the destination floating-point data register.

#### FADD will round the result to the precision selected in the floating-point control register.

#### FSADD and FDADD will round the result to single or double-precision, respectively,

#### regardless of the rounding precision selected in the floating-point control register.

#### Operation Table:

1. If either operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Returns + 0.0 in rounding modes RN, RZ, and RP; returns – 0.0 in RM.
3. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
In Range +
```
**-** Add Add + inf – inf
**Zero +
-** Add

###### + 0.0 0.0^2

```
0.0^2 – 0.0+ inf – inf
Infinity +
```
**-**

```
+ inf
```
- inf

```
+ inf
```
- inf

```
+ inf NAN^3
NAN‡ – inf
```

##### Floating Point Instructions

##### 5-12 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FADD Floating-Point Add FADD

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source and the destination are

#### opposite-signed infinities; cleared otherwise.

#### OVFL Refer to exception processing in the

#### appropriate user’s manual.

#### UNFL Refer to exception processing in the

#### appropriate user’s manual.

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-13

# FADD Floating-Point Add FADD

#### (MC6888X, MC68040)

#### If R/M = 1, specifies the location of the source operand location. Only data

#### addressing modes can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding will cause an unimplemented data type exception to allow

##### emulation in software.

#### Destination Register field—Specifies the destination floating- point data register.

#### Opmode field—Specifies the instruction and rounding precision.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011

#### 0100010 FADD Rounding precision specified by the floating-point control

#### register.

#### 1100010 FSADD Single-precision rounding specified.

#### 1100110 FDADD Double-precision rounding specified.


##### Floating Point Instructions

##### 5-14 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FASIN Arc Sine FASIN

#### (MC6888X, M68040FPSP)

#### Operation: Arc Sine of the Source → FPn

#### Assembler FASIN. < fmt > < ea > ,FPn

#### Syntax: FASIN.X FPm,FPn

#### FASIN.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the arc sine of the number. Stores the result in the destination floating-point

#### data register. This function is not defined for source operands outside of the range [ –

#### 1... + 1]; if the source is not in the correct range, a NAN is returned as the result and

#### the OPERR bit is set in the floating- point status register. If the source is in the correct

#### range, the result is in the range of [ – π/2... + π/2].

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Arc Sine + 0.0 – 0.0 NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-15

# FASIN Arc Sine FASIN

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is infinity, > + 1 or < – 1;

#### cleared otherwise

#### OVFL Cleared

#### UNFL Can be set for an underflow condition.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 1 1 0 0


##### Floating Point Instructions

##### 5-16 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FASIN Arc Sine FASIN

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is then written

#### into the same register. If the single register syntax is used, Motorola assemblers

#### set the source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-17

# FATAN Arc Tangent FATAN

#### (MC6888X, M68040FPSP)

#### Operation: Arc Tangent of Source → FPn

#### Assembler FATAN. < fmt > < ea > ,FPn

#### Syntax: FATAN.X FPm,FPn

#### FATAN.X FPm,FPnz

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the arc tangent of that number. Stores the result in the destination floating-

#### point data register. The result is in the range of [ – π/2... + π/2].

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result Arc Tangent + 0.0 – 0.0 + π/2 – π/2
```

##### Floating Point Instructions

##### 5-18 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FATAN Arc Tangent FATAN

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 1 1 0 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-19

# FATAN Arc Tangent FATAN

#### (MC6888X, M68040FPSP)

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is then written

#### into the same register. If the single register syntax is used, Motorola assemblers

#### set the source and destination fields to the same value.


##### Floating Point Instructions

##### 5-20 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FATANH Hyperbolic Arc Tangent FATANH

#### (MC6888X, M68040FPSP)

#### Operation: Hyperbolic Arc Tangent of Source → FPn

#### Assembler FATANH. < fmt > < ea > ,FPn

#### Syntax: FATANH.X FPm,FPn

#### FATANH.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the hyperbolic arc tangent of that value. Stores the result in the destination

#### floating-point data register. This function is not defined for source operands outside of

#### the range ( – 1... + 1); and the result is equal to – infinity or + infinity if the source is

#### equal to + 1 or – 1, respectively. If the source is outside of the range [ – 1... + 1], a NAN

#### is returned as the result, and the OPERR bit is set in the floating-point status register.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Arc TangentHyperbolic + 0.0 – 0.0 NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-21

# FATANH Hyperbolic Arc Tangent FATANH

#### (MC6888X, M68040FPSP)

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is > + 1 or < – 1; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Set if the source is equal to + 1 or – 1; cleared

#### otherwise.

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0001101


##### Floating Point Instructions

##### 5-22 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FATANH Hyperbolic Arc Tangent FATANH

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is then written

#### into the same register. If the single register syntax is used, Motorola assemblers

#### set the source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-23

# FBcc Floating-Point Branch Conditionally FBcc

#### (MC6888X, MC68040)

#### Operation: If Condition True

#### Then PC + dn → PC

#### Assembler:

#### Syntax: FBcc. < size > , < label >

#### Attributes: Size = (Word, Long)

#### Description: If the specified floating-point condition is met, program execution continues at

#### the location (PC) + displacement. The displacement is a twos-complement integer that

#### counts the relative distance in bytes. The value of the program counter used to

#### calculate the destination address is the address of the branch instruction plus two. If

#### the displacement size is word, then a 16- bit displacement is stored in the word

#### immediately following the instruction operation word. If the displacement size is long

#### word, then a 32-bit displacement is stored in the two words immediately following the

#### instruction operation word. The conditional specifier cc selects any one of the 32

#### floating- point conditional tests as described in 3.6.2 Conditional Testing.

#### Floating-Point Status Register:

#### Condition Codes: Not affected.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Set if the NAN condition code is set and the

#### condition selected is an IEEE nonaware test.

#### SNAN Not Affected.

#### OPERR Not Affected.

#### OVF Not Affected.

#### UNFL Not Affected.

#### DZ Not Affected.

#### INEX2 Not Affected.

#### INEX1 Not Affected.

#### Accrued Exception Byte: The IOP bit is set if the BSUN bit is set in the exception

#### byte. No other bit is affected.


##### Floating Point Instructions

##### 5-24 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FBcc Floating-Point Branch Conditionally FBcc

#### (MC6888X, MC68040)

#### Instruction Format:

#### Instruction Fields:

#### Size field—Specifies the size of the signed displacement.

#### If Format = 0, then the displacement is 16 bits and is sign- extended before use.

#### If Format = 1, then the displacement is 32 bits.

#### Conditional Predicate field—Specifies one of 32 conditional tests as defined in Table

#### 3-23 Floating-Point Conditional Tests.

#### NOTE

#### When a BSUN exception occurs, the main processor takes a

#### preinstruction exception. If the exception handler returns without

#### modifying the image of the program counter on the stack frame

#### (to point to the instruction following the FBcc), then it must clear

#### the cause of the exception (by clearing the NAN bit or disabling

#### the BSUN trap), or the exception will occur again immediately

#### upon return to the routine that caused the exception.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111 COPROCESSORID 0 1 SIZE CONDITIONAL PREDICATE
16-BIT DISPLACEMENT OR MOST SIGNIFICANT WORD OF 32-BITDISPLACEMENT
LEAST SIGNIFICANT WORD OF 32-BIT DISPLACEMENT (IF NEEDED)
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-25

# FCMP Floating-Point Compare FCMP

#### (MC6888X, MC68040)

#### Operation: FPn – Source

#### Assembler FCMP. < fmt > < ea > ,FPn

#### Syntax: FCMP.X FPm,FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### subtracts the operand from the destination floating- point data register. The result of the

#### subtraction is not retained, but it is used to set the floating-point condition codes as

#### described in 3.6.2 Conditional Testing.

#### Operation Table: The entries in this operation table differ from those of the tables

#### describing most of the floating-point instructions. For each combination of input

#### operand types, the condition code bits that may be set are indicated. If the name of a

#### condition code bit is given and is not enclosed in brackets, then it is always set. If the

#### name of a condition code bit is enclosed in brackets, then that bit is either set or

#### cleared, as appropriate. If the name of a condition code bit is not given, then that bit is

#### always cleared by the operation. The infinity bit is always cleared by the FCMP

#### instruction since it is not used by any of the conditional predicate equations. Note that

#### the NAN bit is not shown since NANs are always handled in the same manner (as

#### described in 1.6.5 Not-A-Numbers ).

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
In Range +
```
**-**

```
{NZ}N none {NZ}noneN none NN N none none
```
```
Zero +
```
**-**

```
N N none noneZ NZ NZZ N N none none
```
```
Infinity +
```
**-**

```
noneN noneNnoneN noneNZ N none NZ
```

##### Floating Point Instructions

##### 5-26 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FCMP Floating-Point Compare FCMP

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in the preceding operation table.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 1 1 0 0


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-27

# FCMP Floating-Point Compare FCMP

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand location. Only data

#### addressing modes can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding in the MC68040 will cause an unimplemented data type

##### exception to allow emulation in software.

#### Destination Register field—Specifies the destination floating- point data register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-28 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FCOS Cosine FCOS

#### (MC6888X, M68040FPSP)

#### Operation: Cosine of Source → FPn

#### Assembler FCOS. < fmt > < ea > ,FPn

#### Syntax: FCOS.X FPm,FPn FCOS.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the cosine of that number. Stores the result in the destination floating-point

#### data register. This function is not defined for source operands of ± infinity. If the source

#### operand is not in the range of [ – 2π... + 2π], then the argument is reduced to within that

#### range before the cosine is calculated. However, large arguments may lose accuracy

#### during reduction, and very large arguments (greater than approximately 10^20 ) lose all

#### accuracy. The result is in the range of [ – 1... + 1].

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Cosine + 1.0 NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-29

# FCOS Cosine FCOS

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source operand is ± infinity; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0011101


##### Floating Point Instructions

##### 5-30 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FCOS Cosine FCOS

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should contain zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-31

# FCOSH Hyperbolic Cosine FCOSH

#### (MC6888X, M68040FPSP)

#### Operation: Hyperbolic Cosine of Source → FPn

#### Assembler FCOSH. < fmt > < ea > ,FPn

#### Syntax: FCOSH.X FPm,FPn FCOSH.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the hyperbolic cosine of that number. Stores the result in the destination

#### floating-point data register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result Hyperbolic Cosine + 1.0 + inf
```

##### Floating Point Instructions

##### 5-32 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FCOSH Hyperbolic Cosine FCOSH

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0011101
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-33

# FCOSH Hyperbolic Cosine FCOSH

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### 5-34 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FDBcc Floating-Point Test Condition, FDBcc

## Decrement, and Branch

#### (MC6888X, MC68040)

#### Operation: If Condition True

#### Then No Operation

#### Else Dn – 1 → Dn

#### If Dn ≠ – 1

#### Then PC + dn → PC

#### Else Execute Next Instruction

#### Assembler

#### Syntax: FDBcc Dn, < label >

#### Attributes: Unsized

#### Description: This instruction is a looping primitive of three parameters: a floating-point

#### condition, a counter (data register), and a 16-bit displacement. The instruction first tests

#### the condition to determine if the termination condition for the loop has been met, and if

#### so, execution continues with the next instruction in the instruction stream. If the

#### termination condition is not true, the low-order 16 bits of the counter register are

#### decremented by one. If the result is – 1, the count is exhausted, and execution

#### continues with the next instruction. If the result is not equal to – 1, execution continues

#### at the location specified by the current value of the program counter plus the sign-

#### extended 16-bit displacement. The value of the program counter used in the branch

#### address calculation is the address of the displacement word.

#### The conditional specifier cc selects any one of the 32 floating- point conditional tests

#### as described in 3.6.2 Conditional Testing.

#### Floating-Point Status Register:

#### Condition Codes: Not affected.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Set if the NAN condition code is set and the

#### condition selected is an IEEE nonaware test.

#### SNAN Not Affected.

#### OPERR Not Affected.

#### OVFL Not Affected.

#### UNFL Not Affected.

#### DZ Not Affected.

#### NEX2 Not Affected.

#### INEX1 Not Affected.

#### Accrued Exception Byte: The IOP bit is set if the BSUN bit is set in the exception

#### byte. No other bit is affected.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-35

# FDBcc Floating-Point Test Condition, FDBcc

## Decrement, and Branch

#### (MC6888X, MC68040)

#### Instruction Format:

#### Instruction Fields:

#### Count Register field—Specifies data register that is used as the counter.

#### Conditional Predicate field—Specifies one of the 32 floating-point conditional tests as

#### described in 3.6.2 Conditional Testing.

#### Displacement field—Specifies the branch distance (from the address of the instruction

#### plus two) to the destination in bytes.

#### NOTE

#### The terminating condition is like that defined by the UNTIL loop

#### constructs of high-level languages. For example: FDBOLT can

#### be stated as "decrement and branch until ordered less than".

#### There are two basic ways of entering a loop: at the beginning or

#### by branching to the trailing FDBcc instruction. If a loop structure

#### terminated with FDBcc is entered at the beginning, the control

#### counter must be one less than the number of loop executions

#### desired. This count is useful for indexed addressing modes and

#### dynamically specified bit operations. However, when entering a

#### loop by branching directly to the trailing FDBcc instruction, the

#### count should equal the loop execution count. In this case, if the

#### counter is zero when the loop is entered, the FDBcc instruction

#### does not branch, causing a complete bypass of the main loop.

#### When a BSUN exception occurs, a preinstruction exception is

#### taken by the main processor. If the exception handler returns

#### without modifying the image of the program counter on the stack

#### frame (to point to the instruction following the FDBcc), then it

#### must clear the cause of the exception (by clearing the NAN bit or

#### disabling the BSUN trap), or the exception will occur again im-

#### mediately upon return to the routine that caused the exception.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^001001) REGISTER COUNT
0000000000 CONDITIONAL PREDICATE
16-BIT DISPLACEMENT


##### Floating Point Instructions

##### 5-36 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FDIV Floating-Point Divide FDIV

#### (MC6888X, MC68040)

#### Operation: FPn ÷ Source → FPn

#### Assembler FDIV. < fmt > < ea > ,FPn

#### Syntax: FDIV.X FPm,FPn

#### *FrDIV. < fmt > < ea > ,FPn

#### *FrDIV.X FPm,FPn

#### where r is rounding precision, S or D

##### *Supported by MC68040 only

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and divides

#### that number into the number in the destination floating-point data register. Stores the

#### result in the destination floating-point data register.

#### FDIV will round the result to the precision selected in the floating-point control register.

#### FSDIV and FDDIV will round the result to single or double precision, respectively,

#### regardless of the rounding precision selected in the floating-point control register.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the DZ bit in the floating-point status register exception byte.
3. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
In Range +
```
**-** Divide

```
+ inf^2 – inf^2
```
- inf^2 + inf^2

###### + 0.0 – 0.0

###### – 0.0 + 0.0

```
Zero +
```
**-**

###### + 0.0 + 0.0

###### – 0.0 + 0.0 NAN^3

###### + 0.0– 0.0 – 0.0 + 0.0

```
Infinity +
```
**-**

```
+ inf – inf
```
- inf + inf

```
+ inf – inf
```
- inf + inf NAN‡


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-37

# FDIV Floating-Point Divide FDIV

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set for 0 ÷ 0 or infinity ÷ infinity; cleared

#### otherwise.

#### OVFL Refer to exception processing in the

#### appropriate user’s manual.

#### UNFL Refer to exception processing in the

#### appropriate user’s manual.

#### DZ Set if the source is zero and the destination is

#### in range; cleared otherwise.

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE


##### Floating Point Instructions

##### 5-38 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FDIV Floating-Point Divide FDIV

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand location. Only data

#### addressing modes can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding in the MC68040 will cause an unimplemented data type

##### exception to allow emulation in software.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-39

# FDIV Floating-Point Divide FDIV

#### (MC6888X, MC68040)

#### Destination Register field—Specifies the destination floating- point data register.

#### Opmode field—Specifies the instruction and rounding precision.

#### 0100000 FDIV Rounding precision specified by the floating- point

#### control register.

#### 1100000 FSDIV Single-precision rounding specified.

#### 1100100 FDDIV Double-precision rounding specified.


##### Floating Point Instructions

##### 5-40 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FETOX ex FETOX

#### (MC6888X, M68040FPSP)

#### Operation: eSource → FPn

#### Assembler FETOX. < fmt > < ea > ,FPn

#### Syntax: FETOX.X FPm,FPn

#### Syntax: FETOX.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates e to the power of that number. Stores the result in the destination floating-

#### point data register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result ex + 1.0 + inf + 0.0
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-41

# FETOX ex FETOX

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 1 1 0 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-42 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FETOX ex FETOX

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier Field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-43

# FETOXM1 ex – 1 FETOXM1

#### (MC6888X, M68040FPSP)

#### Operation: eSource – 1 → FPn

#### Assembler FETOXM1. < fmt > < ea > ,FPn

#### Syntax: FETOXM1.X FPm,FPn

#### FETOXM1.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates e to the power of that number. Subtracts one from the value and stores the

#### result in the destination floating-point data register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result ex – 1 + 0.0 – 0.0 + inf – 1.0
```

##### Floating Point Instructions

##### 5-44 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FETOXM1 ex – 1 FETOXM1

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 1 1 0 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-45

# FETOXM1 ex – 1 FETOXM1

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier Field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### 5-46 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FGETEXP Get Exponent FGETEXP

#### (MC6888X, M68040FPSP)

#### Operation: Exponent of Source → FPn

#### Assembler FGETEXP. < fmt > < ea > ,FPn

#### Syntax: FGETEXP.X FPm,FPn

#### FGETEXP.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### extracts the binary exponent. Removes the exponent bias, converts the exponent to an

#### extended-precision floating- point number, and stores the result in the destination

#### floating- point data register.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is ± infinity; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Exponent + 0.0 – 0.0 NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-47

# FGETEXP Get Exponent FGETEXP

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 1 1 1 1 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-48 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FGETEXP Get Exponent FGETEXP

#### (MC6888X, M68040FPSP)

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-49

# FGETMAN Get Mantissa FGETMAN

#### (MC6888X, M68040FPSP)

#### Operation: Mantissa of Source → FPn

#### Assembler FGETMAN. < fmt > < ea > ,FPn

#### Syntax: FGETMAN.X FPm,FPn

#### FGETMAN.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### extracts the mantissa. Converts the mantissa to an extended-precision value and

#### stores the result in the destination floating-point data register. The result is in the range

#### [1.0...2.0] with the sign of the source mantissa, zero, or a NAN.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is ± infinity; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Mantissa + 0.0 – 0.0 NAN^2
```

##### Floating Point Instructions

##### 5-50 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FGETMAN Get Mantissa FGETMAN

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0011111
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-51

# FGETMAN Get Mantissa FGETMAN

#### (MC6888X, M68040FPSP)

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### 5-52 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FINT Integer Part FINT

#### (MC6888X, M68040FPSP)

#### Operation: Integer Part of Source → FPn

#### Assembler FINT. < fmt > < ea > ,FPn

#### Syntax: FINT.X FPm,FPn

#### FINT.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary), extracts

#### the integer part, and converts it to an extended-precision floating-point number. Stores

#### the result in the destination floating-point data register. The integer part is extracted by

#### rounding the extended-precision number to an integer using the current rounding mode

#### selected in the floating-point control register mode control byte. Thus, the integer part

#### returned is the number that is to the left of the radix point when the exponent is zero,

#### after rounding. For example, the integer part of 137.57 is 137.0 for the round-to-zero

#### and round-to- negative infinity modes and 138.0 for the round-to-nearest and round-to-

#### positive infinity modes. Note that the result of this operation is a floating-point number.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result Integer + 0.0 – 0.0 + inf – inf
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-53

# FINT Integer Part FINT

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0000001


##### Floating Point Instructions

##### 5-54 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FINT Integer Part FINT

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-55

# FINTRZ Integer Part, Round-to-Zero FINTRZ

#### (MC6888X, M68040FPSP)

#### Operation: Integer Part of Source → FPn

#### Assembler FINTRZ. < fmt > < ea > ,FPn

#### Syntax: FINTRZ.X FPm,FPn

#### FINTRZ.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### extracts the integer part and converts it to an extended-precision floating-point number.

#### Stores the result in the destination floating-point data register. The integer part is

#### extracted by rounding the extended-precision number to an integer using the round-to-

#### zero mode, regardless of the rounding mode selected in the floating-point control

#### register mode control byte (making it useful for FORTRAN assignments). Thus, the

#### integer part returned is the number that is to the left of the radix point when the

#### exponent is zero. For example, the integer part of 137.57 is 137.0; the integer part of

#### 0.1245 x 102 is 12.0. Note that the result of this operation is a floating-point number.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result Integer, Forced Round-to- Zero + 0.0 – 0.0 + inf – inf
```

##### Floating Point Instructions

##### 5-56 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FINTRZ Integer Part, Round-to-Zero FINTRZ

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0000011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-57

# FINTRZ Integer Part, Round-to-Zero FINTRZ

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If RM = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-58 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FLOG10 Log 10 FLOG10

#### (MC6888X, M68040FPSP)

#### Operation: Log 10 of Source → FPn

#### Assembler FLOG10. < fmt > < ea > ,FPn

#### Syntax: FLOG10.X FPm,FPn

#### FLOG10.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Convert the source operand to extended precision (if necessary) and

#### calculates the logarithm of that number using base 10 arithmetic. Stores the result in

#### the destination floating-point data register. This function is not defined for input values

#### less than zero.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.
3. Sets the DZ bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source operand is < 0; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Set if the source is ± 0; cleared otherwise

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Log 10 NAN^2 – inf^3 + inf NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-59

# FLOG10 Log 10 FLOG10

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 1 0 1 0 1
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-60 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FLOG10 Log 10 FLOG10

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-61

# FLOG2 Log 2 FLOG2

#### (MC6888X, M68040FPSP)

#### Operation: Log 2 of Source → FPn

#### Assembler FLOG2. < fmt > < ea > ,FPn

#### Syntax: FLOG2.X FPm,FPn

#### FLOG2.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the logarithm of that number using base two arithmetic. Stores the result in

#### the destination floating- point data register. This function is not defined for input values

#### less than zero.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.
3. Sets the DZ bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is < 0; cleared otherwise

#### OVFL Cleared

#### UNFL Cleared

#### DZ Set if the source is ± 0; cleared otherwise

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Log 2 NAN^2 – inf^3 + inf NAN^2
```

##### Floating Point Instructions

##### 5-62 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FLOG2 Log 2 FLOG2

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 1 0 1 1 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-63

# FLOG2 Log 2 FLOG2

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### 5-64 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FLOGN Loge FLOGN

#### (MC6888X, M68040FPSP)

#### Operation: Loge of Source → FPn

#### Assembler FLOGN. < fmt > < ea > ,FPn

#### Syntax: FLOGN.X FPm,FPn

#### FLOGN.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the natural logarithm of that number. Stores the result in the destination

#### floating-point data register. This function is not defined for input values less than zero.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.
3. Sets the DZ bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source operand is < 0; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Set if the source is ± 0; cleared otherwise

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result In(x) NAN^2 – inf^3 + inf NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-65

# FLOGN Loge FLOGN

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 1 0 1 0 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-66 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FLOGN Loge FLOGN

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-67

# FLOGNP1 Loge (x + 1) FLOGNP1

#### (MC6888X, M68040FPSP)

#### Operation: Loge of (Source + 1) → FPn

#### Assembler FLOGNP1. < fmt > < ea > ,FPn

#### Syntax: FLOGNP1.X FPm,FPn

#### FLOGNP1.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary), adds one

#### to that value, and calculates the natural logarithm of that intermediate result. Stores the

#### result in the destination floating-point data register. This function is not defined for input

#### values less than – 1.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. If the source is – 1, sets the DZ bit in the floating-point status register
    exception byte and returns a NAN. If the source is < – 1, sets the OPERR bit
    in the floating-point status register exception byte and returns a NAN.
3. Sets the OPERR bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result In(x + 1) In(x + 1)^2 + 0.0 – 0.0+ inf NAN^23
```

##### Floating Point Instructions

##### 5-68 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FLOGNP1 Loge (x + 1) FLOGNP1

#### (MC6888X, M68040FPSP)

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source operand is < – 1; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Set if the source operand is – 1; cleared

#### otherwise

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 0 1 1 0


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-69

# FLOGNP1 Loge (x + 1) FLOGNP1

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-70 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOD Modulo Remainder FMOD

#### (MC6888X, M68040FPSP)

#### Operation: Modulo Remainder of (FPn ÷ Source) → FPn

#### Assembler FMOD. < fmt > < ea > ,FPn

#### Syntax: FMOD.X FPm,FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the modulo remainder of the number in the destination floating-point data

#### register, using the source operand as the modulus. Stores the result in the destination

#### floating-point data register and stores the sign and seven least significant bits of the

#### quotient in the floating-point status register quotient byte (the quotient is the result of

#### FPn ÷ Source). The modulo remainder function is defined as:

#### FPn – (Source x N)

#### where N = INT(FPn ÷ Source) in the round-to-zero mode.

#### The FMOD function is not defined for a source operand equal to zero or for a destination

#### operand equal to infinity. Note that this function is not the same as the FREM instruction,

#### which uses the round-to-nearest mode and thus returns the remainder that is required by

#### the IEEE Specification for Binary Floating-Point Arithmetic.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.
3. Returns the value of FPn before the operation. However, the result is
    processed by the normal instruction termination procedure to round it as
    required. Thus, an overflow and/or inexact result may occur if the rounding
    precision has been changed to a smaller size since the FPn value was
    loaded

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero# – + Infinity –

```
In Range +
```
**-** Modulo Remainder NAN

(^2) FPn 3
**Zero +**

**-**

###### + 0.0

###### – 0.0 NAN

###### 2 + 0.0

###### – 0.0

```
Infinity +
```
**-** NAN

(^2) NAN (^2) NAN (^2)


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-71

# FMOD Modulo Remainder FMOD

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Loaded with the sign and least significant seven bits of the

#### quotient (FPn ÷ Source). The sign of the quotient is the

#### exclusive-OR of the sign bits of the source and destination

#### operands.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is zero or the destination is

#### infinity; cleared otherwise.

#### OVFL Cleared

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, in the appropriate user’s

#### manual for inexact result on decimal input;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0101101


##### Floating Point Instructions

##### 5-72 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOD Modulo Remainder FMOD

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-73

# FMOVE Move Floating-Point Data Register FMOVE

#### (MC6888X, MC68040)

#### Operation: Source → Destination

#### Assembler FMOVE. < fmt > < ea > ,FPn

#### Syntax: FMOVE. < fmt > FPm, < ea >

#### FMOVE.P FPm, < ea > {Dn}

#### FMOVE.P FPm, < ea > {k}

#### *FrMOVE. < fmt > < ea > ,FPn

#### where r is rounding precision, S or D

##### *Supported by MC68040 only

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Moves the contents of the source operand to the destination operand.

#### Although the primary function of this instruction is data movement, it is also considered

#### an arithmetic instruction since conversions from the source operand format to the

#### destination operand format are performed implicitly during the move operation. Also,

#### the source operand is rounded according to the selected rounding precision and mode.

#### Unlike the MOVE instruction, the FMOVE instruction does not support a memory-to-

#### memory format. For such transfers, it is much faster to utilize the MOVE instruction to

#### transfer the floating- point data than to use the FMOVE instruction. The FMOVE

#### instruction only supports memory-to-register, register-to- register, and register-to-

#### memory operations (in this context, memory may refer to an integer data register if the

#### data format is byte, word, long, or single). The memory-to-register and register- to-reg-

#### ister operation uses a command word encoding distinctly different from that used by

#### the register-to-memory operation; these two operation classes are described sepa-

#### rately.

#### Memory-to-Register and Register-to-Register Operation: Converts the source operand

#### to an extended-precision floating-point number (if necessary) and stores it in the

#### destination floating-point data register. MOVE will round the result to the precision

#### selected in the floating-point control register. FSMOVE and FDMOVE will round the

#### result to single or double precision, respectively, regardless of the rounding precision

#### selected in the floating-point control register. Depending on the source data format and

#### the rounding precision, some operations may produce an inexact result. In the following

## table, combinations that can produce an inexact result are marked with a dot (⋅), but all

#### other combinations produce an exact result.


##### Floating Point Instructions

##### 5-74 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVE Move Floating-Point Data Register FMOVE

#### (MC6888X, MC68040)

#### Floating-Point Status Register ( < ea > to Register):

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Refer to exception processing in the

#### appropriate user’s manual if the source is an

#### extended-precision denormalized number;

#### cleared otherwise.

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual if < fmt > is L,D, or

#### X; cleared otherwise.

#### INEX1 Refer to exception processing in the

#### appropriate user’s manual if < fmt > is P;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

```
Rounding
Precision
```
```
Source Format
B W L S D X P
```
## Single ⋅⋅⋅⋅

## Double ⋅⋅

## Extended ⋅


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-75

# FMOVE Move Floating-Point Data Register FMOVE

#### (MC6888X, MC68040)

#### Instruction Format:

##### < EA > TO REGISTER

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand. Only data addressing modes

#### can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-76 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVE Move Floating-Point Data Register FMOVE

#### (MC6888X, MC68040)

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding in the MC68040 will cause an unimplemented data type

##### exception to allow emulation in software.

#### Destination Register field—Specifies the destination floating- point data register.

#### Opmode field—Specifies the instruction and rounding precision.

#### Register-to-Memory Operation: Rounds the source operand to the size of the specified

#### destination format and stores it at the destination effective address. If the format of the

#### destination is packed decimal, a third operand is required to specify the format of the

#### resultant string. This operand, called the k-factor, is a 7-bit signed integer (twos

#### complement) and may be specified as an immediate value or in an integer data

#### register. If a data register contains the k-factor, only the least significant seven bits are

#### used, and the rest of the register is ignored.

#### 0000000 FMOVE Rounding precision specified by the floating-point

#### control register.

#### 1000000 FSMOVE Single-precision rounding specified.

#### 1000100 FDMOVE Double-precision rounding specified.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-77

# FMOVE Move Floating-Point Data Register FMOVE

#### (MC6888X, MC68040)

#### Floating-Point Status Register (Register-to-Memory):

#### Condition Codes: Not affected.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### < fmt > is B, W, or L SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source operand is infinity or if the

#### destination size is exceeded after conversion

#### and rounding; cleared otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 Cleared

#### < fmt > is S, D, or X BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers

#### OVFL Refer to exception processing in the

#### appropriate user’s manual.

#### UNFL Refer to exception processing in the

#### appropriate user’s manual.

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 Cleared

#### < fmt > is P BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the k-factor > + 17 or the magnitude of

#### the decimal exponent exceeds three digits;

#### cleared otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 Cleared

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.


##### Floating Point Instructions

##### 5-78 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVE Move Floating-Point Data Register FMOVE

#### (MC6888X, MC68040)

#### Instruction Format:

##### REGISTER—TO-MEMORY

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### Destination Format field—Specifies the data format of the destination operand:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real with Static k-Factor (P{#k})*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### 111 — Packed-Decimal Real with Dynamic k-Factor (P{Dn})*

##### *This encoding will cause an unimplemented data type exception in the

##### MC68040 to allow emulation in software.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
111 COPROCESSORID (^1000) MODEEFFECTIVE ADDRESS REGISTER
011 DESTINATIONFORMAT REGISTERSOURCE (IF REQUIRED) K-FACTOR
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-79

# FMOVE Move Floating-Point Data Register FMOVE

#### (MC6888X, MC68040)

#### Source Register field—Specifies the source floating-point data register.

#### k-Factor field—If the destination format is packed decimal, used to specify the format

#### of the decimal string. For any other destination format, this field should be set to

#### all zeros. For a static k-factor, this field is encoded with a twos-complement

#### integer where the value defines the format as follows:

- 64 to 0—Indicates the number of significant digits to the right of the decimal

#### point (FORTRAN "F" format).

#### + 1 to + 17—Indicates the number of significant digits in the mantissa (FOR-

#### TRAN "E" format).

#### + 18 to + 63—Sets the OPERR bit in the floating-point status register exception

#### byte and treated as + 17.

#### The format of this field for a dynamic k-factor is:

#### r r r 0 0 0 0

#### where "rrr" is the number of the main processor data register that contains the k-factor

#### value.

#### The following table gives several examples of how the k-factor value affects the format

#### of the decimal string that is produced by the floating-point coprocessor. The format of

#### the string that is generated is independent of the source of the k-factor (static or

#### dynamic).

```
k- Factor Source Operand Value Destination String
```
- 5 + 12345.678765 + 1.234567877E + 4
- 3 + 12345.678765 + 1.2345679E + 4
- 1 + 12345.678765 + 1.23457E + 4
    0 + 12345.678765 + 1.2346E + 4
+ 1 + 12345.678765 + 1.E + 4
+ 3 + 12345.678765 + 1.23E + 4
+ 5 + 12345.678765 + 1.2346E + 4


##### Floating Point Instructions

##### 5-80 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVE Move Floating-Point FMOVE

## System Control Register

#### (MC6888X, MC68040)

#### Operation: Source → Destination

#### Assembler FMOVE.L < ea > ,FPCR

#### Syntax: FMOVE.L FPCR, < ea >

#### Attributes: Size = (Long)

#### Description: Moves the contents of a floating-point system control register (floating-point

#### control register, floating-point status register, or floating-point instruction address

#### register) to or from an effective address. A 32-bit transfer is always performed, even

#### though the system control register may not have 32 implemented bits. Unimplemented

#### bits of a control register are read as zeros and are ignored during writes (must be zero

#### for compatibility with future devices). For the MC68881, this instruction does not cause

#### pending exceptions (other than protocol violations) to be reported. Furthermore, a write

#### to the floating-point control register exception enable byte or the floating-point status

#### register exception status byte cannot generate a new exception, regardless of the

#### value written.

#### Floating-Point Status Register: Changed only if the destination is the floating-point status

#### register, in which case all bits are modified to reflect the value of the source operand.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
1 0 dr REGISTERSELECT 0000000000


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-81

# FMOVE Move Floating-Point FMOVE

## System Control Register

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—(Memory-to-Register) All addressing modes can be used as

#### listed in the following table:

```
*Only if the source register is the floating-point instruction address register.
```
#### Effective Address field—(Register-to-Memory) Only alterable addressing modes can

#### be used as listed in the following table:

```
*Only if the source register is the floating-point instruction address register.
```
```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Floating Point Instructions

##### 5-82 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVE Move Floating-Point FMOVE

## System Control Register

#### (MC6888X, MC68040)

#### dr field—Specifies the direction of the data transfer.

#### 0 — From < ea > to the specified system control register.

#### 1 — From the specified system control register to < ea >.

#### Register Select field—Specifies the system control register to be moved:

#### 100 Floating-Point Control Register

#### 010 Floating-Point Status Register

#### 001 Floating-Point Instruction Address Register


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-83

# FMOVECR Move Constant ROM FMOVECR

#### (MC6888X, M68040FPSP)

#### Operation: ROM Constant → FPn

#### Assembler

#### Syntax: FMOVECR.X # < ccc > ,FPn

#### Attributes: Format = (Extended)

#### Description: Fetches an extended-precision constant from the floating- point coprocessor

#### on-chip ROM, rounds the mantissa to the precision specified in the floating-point

#### control register mode control byte, and stores it in the destination floating-point data

#### register. The constant is specified by a predefined offset into the constant ROM. The

#### values of the constants contained in the ROM are shown in the offset table at the end

#### of this description.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Cleared

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 Cleared

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111 COPROCESSORID 0 0 0 0 0 0 0 0 0
010111 DESTINATIONREGISTER ROM OFFSET
```

##### Floating Point Instructions

##### 5-84 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVECR Move Constant ROM FMOVECR

#### (MC6888X, M68040FPSP)

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Destination Register field—Specifies the destination floating- point data register.

#### ROM Offset field—Specifies the offset into the floating-point coprocessor on-chip

#### constant ROM where the desired constant is located. The offsets for the available

#### constants are as follows:

#### The on-chip ROM contains other constants useful only to the on- chip microcode rou-

#### tines. The values contained at offsets other than those defined above are reserved for

#### the use of Motorola and may be different on various mask sets of the floating-point

#### coprocessor. These undefined values yield the value 0.0 in the M68040FPSP.

#### Offset Constant

#### $00 π

#### $0B Log 10 (2)

#### $0C e

#### $0D Log 2 (e)

#### $0E Log 10 (e)

#### $0F 0.0

#### $30 1n(2)

#### $31 1n(10)

#### $32 100

#### $33 101

#### $34 102

#### $35 104

#### $36 108

#### $37 1016

#### $38 1032

#### $39 1064

#### $3A 10128

#### $3B 10256

#### $3C 10512

#### $3D 101024

#### $3E 102048

#### $3F 104096


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-85

# FMOVEM Move Multiple Floating-Point FMOVEM

## Data Registers

#### (MC6888X, MC68040)

#### Operation: Register List → Destination

#### Source → Register List

#### Assembler FMOVEM.X < list > , < ea >

#### Syntax: FMOVEM.X Dn, < ea >

#### FMOVEM.X < ea > , < list > FMOVEM.X < ea > ,Dn

#### Attributes: Format = (Extended)

#### Description: Moves one or more extended-precision numbers to or from a list of floating-

#### point data registers. No conversion or rounding is performed during this operation, and

#### the floating-point status register is not affected by the instruction. For the MC68881, this

#### instruction does not cause pending exceptions (other than protocol violations) to be

#### reported. Furthermore, a write to the floating- point control register exception enable

#### byte or the floating-point status register exception status byte connot generate a new

#### exception, despite the value written.

#### Any combination of the eight floating-point data registers can be transferred, with the

#### selected registers specified by a user- supplied mask. This mask is an 8-bit number,

#### where each bit corresponds to one register; if a bit is set in the mask, that register is

#### moved. The register select mask may be specified as a static value contained in the

#### instruction or a dynamic value in the least significant eight bits of an integer data reg-

#### ister (the remaining bits of the register are ignored).

#### FMOVEM allows three types of addressing modes: the control modes, the predecre-

#### ment mode, or the postincrement mode. If the effective address is one of the control

#### addressing modes, the registers are transferred between the processor and memory

#### starting at the specified address and up through higher addresses. The order of the

#### transfer is from FP0 – FP7.


##### Floating Point Instructions

##### 5-86 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVEM Move Multiple Floating-Point FMOVEM

## Data Registers

#### (MC6888X, MC68040)

#### If the effective address is the predecrement mode, only a register- to-memory opera-

#### tion is allowed. The registers are stored starting at the address contained in the

#### address register and down through lower addresses. Before each register is stored, the

#### address register is decremented by 12 (the size of an extended-precision number in

#### memory) and the floating-point data register is then stored at the resultant address.

#### When the operation is complete, the address register points to the image of the last

#### floating- point data register stored. The order of the transfer is from FP7 – FP0.

#### If the effective address is the postincrement mode, only a memory- to-register opera-

#### tion is allowed. The registers are loaded starting at the specified address and up

#### through higher addresses. After each register is stored, the address register is incre-

#### mented by 12 (the size of an extended-precision number in memory). When the oper-

#### ation is complete, the address register points to the byte immediately following the

#### image of the last floating-point data register loaded. The order of the transfer is the

#### same as for the control addressing modes: FP0 – FP7.

#### Floating-Point Status Register: Not Affected. Note that the FMOVEM instruction provides

#### the only mechanism for moving a floating- point data item between the floating-point

#### unit and memory without performing any data conversions or affecting the condition

#### code and exception status bits.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1 1 1 1 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
1 1 dr MODE 0 0 0 REGISTER LIST


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-87

# FMOVEM Move Multiple Floating-Point FMOVEM

## Data Registers

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—(Memory-to-Register) Only control addressing modes or the

#### postincrement addressing mode can be used as listed in the following table:

#### Effective Address field—(Register-to-Memory) Only control alterable addressing

#### modes or the predecrement addressing mode can be used as listed in the

#### following table:

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
```
- (An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Floating Point Instructions

##### 5-88 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVEM Move Multiple Floating-Point FMOVEM

## Data Registers

#### (MC6888X, MC68040)

#### dr field—Specifies the direction of the transfer.

#### 0 — Move the listed registers from memory to the floating-point unit.

#### 1 — Move the listed registers from the floating-point unit to memory.

#### Mode field—Specifies the type of the register list and addressing mode.

#### 00 — Static register list, predecrement addressing mode.

#### 01 — Dynamic register list, predecrement addressing mode.

#### 10 — Static register list, postincrement or control addressing mode.

#### 11 — Dynamic register list, postincrement or control addressing mode.

#### Register List field:

#### Static list—contains the register select mask. If a register is to be moved, the corre-

#### sponding bit in the mask is set as shown below; otherwise it is clear.

#### Dynamic list—contains the integer data register number, rrr, as listed in the following

#### table:

#### The format of the dynamic list mask is the same as for the static list and is contained

#### in the least significant eight bits of the specified main processor data register.

#### Programming Note: This instruction provides a very useful feature, dynamic register list

#### specification, that can significantly enhance system performance. If the calling

#### conventions used for procedure calls utilize the dynamic register list feature, the

#### number of floating-point data registers saved and restored can be reduced.

#### To utilize the dynamic register specification feature of the FMOVEM instruction, both

#### the calling and the called procedures must be written to communicate information

#### about register usage. When one procedure calls another, a register mask must be

#### passed to the called procedure to indicate which registers must not be altered upon

#### return to the calling procedure. The called procedure then saves only those registers

#### that are modified and are already in use. Several techniques can be used to utilize this

#### mechanism, and an example follows.

```
List Type Register List Format
Static, – (An) FP7 FP6 FP5 FP4 FP3 FP2 FP1 FP0
Static, (An) + ,
or Control FP0 FP1 FP2 FP3 FP4 FP5 FP6 FP7
Dynamic 0 r r r 0 0 0 0
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-89

# FMOVEM Move Multiple Floating-Point FMOVEM

## Data Registers

#### (MC6888X, MC68040)

#### In this example, a convention is defined by which each called procedure is passed a

#### word mask in D7 that identifies all floating-point registers in use by the calling proce-

#### dure. Bits 15 – 8 identify the registers in the order FP0 – FP7, and bits 7 – 0 identify the

#### registers in the order FP7 – FP0 (the two masks are required due to the different trans-

#### fer order used by the predecrement and postincrement addressing modes). The code

#### used by the calling procedure consists of simply moving the mask (which is generated

#### at compile time) for the floating-point data registers currently in use into D7:

#### Calling procedure...

#### The entry code for all other procedures computes two masks. The first mask identifies

#### the registers in use by the calling procedure that are used by the called procedure (and

#### therefore saved and restored by the called procedure). The second mask identifies the

#### registers in use by the calling procedure that are used by the called procedure (and

#### therefore not saved on entry). The appropriate registers are then stored along with the

#### two masks:

#### Called procedure...

#### If the second procedure calls a third procedure, a register mask is passed to the third

#### procedure that indicates which registers must not be altered by the third procedure.

#### This mask identifies any registers in the list from the first procedure that were not saved

#### by the second procedure, plus any registers used by the second procedure that must

#### not be altered by the third procedure.

#### MOVE.W #ACTIVE,D7 Load the list of FP registers that are

#### in use.

#### BSR PROC_2

#### MOVE.W D7,D6 Copy the list of active registers.

#### AND.W #WILL_USE,D7 Generate the list of doubly-used

#### registers.

#### FMOVEM D7, – (A7) Save those registers.

#### MOVE.W D7, – (A7) Save the register list.

#### EOR.W D7,D6 Generate the list of not saved active

#### registers.

#### MOVE.W D6, – (A7) Save it for later use.


##### Floating Point Instructions

##### 5-90 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVEM Move Multiple Floating-Point FMOVEM

## Data Registers

#### (MC6888X, MC68040)

#### An example of the calculation of this mask is as follows:

#### Nested calling sequence...

#### Upon return from a procedure, the restoration of the necessary registers follows the

#### same convention, and the register mask generated during the save operation on entry

#### is used to restore the required floating-point data registers:

#### Return to caller...

#### MOVE.W UNSAVED (A7),D7 Load the list of active registers not

#### saved at entry.

#### OR.W #WILL_USE,D7 Combine with those active at this time

#### BSR PROC_3

#### ADDQ.L #2,A7 Discard the list of registers not saved.

#### MOVE.B (A7) + ,D7 Get the saved register list (pop word,

#### use byte).

#### FMOVEM (A7) + ,D7 Restore the registers.

#### *

#### *

#### *

#### RTS Return to the calling routine.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-91

# FMOVEM Move Multiple Floating-Point FMOVEM

## Control Registers

#### (MC6888X, MC68040)

#### Operation: Register List → Destination

#### Source → Register List

#### Assembler FMOVEM.L < list > , < ea >

#### Syntax: FMOVEM.L < ea > , < list >

#### Attributes: Size = (Long)

#### Description: Moves one or more 32-bit values into or out of the specified system control

#### registers. Any combination of the three system control registers may be specified. The

#### registers are always moved in the same order, regardless of the addressing mode

#### used; the floating-point control register is moved first, followed by the floating-point

#### status register, and the floating-point instruction address register is moved last. If a

#### register is not selected for the transfer, the relative order of the transfer of the other

#### registers is the same. The first register is transferred between the floating-point unit and

#### the specified address, with successive registers located up through higher addresses.

#### For the MC68881, this instruction does not cause pending exceptions (other than pro-

#### tocol violations) to be reported. Furthermore, a write to the floating-point control regis-

#### ter exception enable byte or the floating-point status register exception status byte

#### connot generate a new exception, despite the value written.

#### When more than one register is moved, the memory or memory- alterable addressing

#### modes can be used as shown in the addressing mode tables. If the addressing mode

#### is predecrement, the address register is first decremented by the total size of the reg-

#### ister images to be moved (i.e., four times the number of registers), and then the regis-

#### ters are transferred starting at the resultant address. For the postincrement addressing

#### mode, the selected registers are transferred to or from the specified address, and then

#### the address register is incremented by the total size of the register images transferred.

#### If a single system control register is selected, the data register direct addressing mode

#### may be used; if the only register selected is the floating-point instruction address reg-

#### ister, then the address register direct addressing mode is allowed. Note that if a single

#### register is selected, the opcode generated is the same as for the FMOVE single system

#### control register instruction.


##### Floating Point Instructions

##### 5-92 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMOVEM Move Multiple Floating-Point FMOVEM

## Control Registers

#### (MC6888X, MC68040)

#### Floating-Point Status Register: Changed only if thedestinationlist includes the floating-

#### point status register in which case all bits are modified to reflect the value of the source

#### register image.

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for the operation.

#### Memory-to-Register—Only control addressing modes or the postincrement

#### addressing mode can be used as listed in the following table:

```
*Only if a single floating-point instruction address register, floating-point status register, or
floating-point control register is selected.
**Only if the floating-point instruction address register is the single register selected.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1 1 1 1 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
1 0 dr REGISTERLIST 0000000000
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An** 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-93

# FMOVEM Move Multiple Floating-Point FMOVEM

## Control Registers

#### (MC6888X, MC68040)

#### Register-to-Memory—Only control alterable addressing modes or the predecrement

#### addressing mode can be used as listed in the following table:

```
*Only if a single floating-point control register is selected.
**Only if the floating-point instruction address register is the single register selected.
```
#### dr field—Specifies the direction of the transfer.

#### 0 — Move the listed registers from memory to the floating-point unit.

#### 1 — Move the listed registers from the floating-point unit to memory.

#### Register List field—Contains the register select mask. If a register is to be moved, the

#### corresponding bit in the list is set; otherwise, it is clear. At least one register must

#### be specified.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An** 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —

```
Bit Number Register
12 Floating-Point Control Register
11 Floating-Point Status Register
10 Floating-Point InstructionAddress Register
```

##### Floating Point Instructions

##### 5-94 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMUL Floating-Point Multiply FMUL

#### (MC6888X, MC68040)

#### Operation: Source x FPn → FPn

#### Assembler FMUL. < fmt > < ea > ,FPn

#### Syntax: FMUL.X FPm,FPn

#### *FrMUL < fmt > < ea > ,FPn

#### *FrMUL.X FPm,FPn

#### where r is rounding precision, S or D

#### *Supported by MC68040 only

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### multiplies that number by the number in the destination floating-point data register.

#### Stores the result in the destination floating-point data register.

#### FMUL will round the result to the precision selected in the floating-point control register.

#### FSMUL and FDMUL will round the result to single or double precision, respectively,

#### regardless of the rounding precision selected in the floating-point control register.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
In Range +
```
**-** Multiply

```
+ 0.0– 0.0 – 0.0 + 0.0+ inf – inf – inf + inf
```
```
Zero +
```
**-**

###### + 0.0– 0.0 – 0.0 + 0.0+ 0.0– 0.0 – 0.0 + 0.0 NAN 2

```
Infinity +
```
**-**

```
+ inf – inf – inf + inf NAN 2 + inf – inf
```
- inf + inf


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-95

# FMUL Floating-Point Multiply FMUL

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set for 0 x infinity; cleared otherwise.

#### OVFL Refer to exception processing in the

#### appropriate user’s manual.

#### UNFL Refer to exception processing in the

#### appropriate user’s manual.

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE


##### Floating Point Instructions

##### 5-96 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FMUL Floating-Point Multiply FMUL

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand location. Only data

#### addressing modes can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding will cause an unimplemented data type exception in the

##### MC68040 to allow emulation in software.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-97

# FMUL Floating-Point Multiply FMUL

#### (MC6888X, MC68040)

#### Destination Register field—Specifies the destination floating- point data register.

#### Opmode field—Specifies the instruction and rounding precision.

#### 0100011 FMUL Rounding precision specified by the floating-point

#### control register.

#### 1100011 FSMUL Single-precision rounding specified.

#### 1100111 FDMUL Double-precision rounding specified.


##### Floating Point Instructions

##### 5-98 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FNEG Floating-Point Negate FNEG

#### (MC6888X, MC68040)

#### Operation: – (Source) → FPn

#### Assembler FNEG. < fmt > < ea > ,FPn

#### Syntax: FNEG.X FPm,FPn

#### FNEG.X FPn

#### *FrNEG. < fmt > < ea > ,FPn

#### *FrNEG.X FPm,FPn

#### *FrNEG.X FPn

#### where r is rounding precision, S or D

#### *Supported by MC68040 only

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and inverts

#### the sign of the mantissa. Stores the result in the destination floating-point data register.

#### FNEG will round the result to the precision selected in the floating-point control register.

#### FSNEG and FDNEG will round the result to single or double precision, respectively,

#### regardless of the rounding precision selected in the floating-point control register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result Negate – 0.0 + 0.0 – inf + inf
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-99

# FNEG Floating-Point Negate FNEG

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL If source is an extended-precision

#### denormalized number, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE


##### Floating Point Instructions

##### 5-100 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FNEG Floating-Point Negate FNEG

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand. Only data addressing modes

#### can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding will cause an unimplemented data type exception to allow

##### emulation in software.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-101

# FNEG Floating-Point Negate FNEG

#### (MC6888X, MC68040)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.

#### Opmode field—Specifies the instruction and rounding precision.

#### 0011010 FNEG Rounding precision specified by the floating-point

#### control register.

#### 1011010 FSNEG Single-precision rounding specified.

#### 1011110 FDNEG Double-precision rounding specified.


##### Floating Point Instructions

##### 5-102 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FNOP No Operation FNOP

#### (MC6888X, MC68040)

#### Operation: None

#### Assembler

#### Syntax: FNOP

#### Attributes: Unsized

#### Description: This instruction does not perform any explicit operation. However, it is useful

#### to force synchronization of the floating- point unit with an integer unit or to force

#### processing of pending exceptions. For most floating-point instructions, the integer unit

#### is allowed to continue with the execution of the next instruction once the floating-point

#### unit has any operands needed for an operation, thus supporting concurrent execution

#### of floating-point and integer instructions. The FNOP instruction synchronizes the

#### floating-point unit and the integer unit by causing the integer unit to wait until all

#### previous floating-point instructions have completed. Execution of FNOP also forces

#### any exceptions pending from the execution of a previous floating-point instruction to be

#### processed as a preinstruction exception.

#### The MC68882 may not wait to begin execution of another floating- point instruction until

#### it has completed execution of the current instruction. The FNOP instruction synchro-

#### nizes the coprocessor and microprocessor unit by causing the microprocessor unit to

#### wait until the current instruction (or both instructions) have completed.

#### The FNOP instruction also forces the processing of exceptions pending from the exe-

#### cution of previous instructions. This is also inherent in the way that the floating-point

#### coprocessor utilizes the M68000 family coprocessor interface. Once the floating-point

#### coprocessor has received the input operand for an arithmetic instruction, it always

#### releases the main processor to execute the next instruction (regardless of whether or

#### not concurrent execution is prevented for the instruction due to tracing) without report-

#### ing the exception during the execution of that instruction. Then, when the main proces-

#### sor attempts to initiate the execution of the next floating-point coprocessor instruction,

#### a preinstruction exception may be reported to initiate exception processing for an

#### exception that occurred during a previous instruction. By using the FNOP instruction,

#### the user can force any pending exceptions to be processed without performing any

#### other operations.

#### Floating-Point Status Register: Not Affected.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-103

# FNOP No Operation FNOP

#### (MC6888X, MC68040)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### NOTE

#### FNOP uses the same opcode as the FBcc.W < label > instruc-

#### tion, with cc = F (nontrapping false) and < label > = + 2 (which

#### results in a displacement of 0).

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111 COPROCESSOR ID 0 1 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
```

##### Floating Point Instructions

##### 5-104 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FREM IEEE Remainder FREM

#### (MC6888X, M68040FPSP)

#### Operation: IEEE Remainder of (FPn ÷ Source) → FPn

#### Assembler FREM. < fmt > < ea > ,FPn

#### Syntax: FREM.X FPm,FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the modulo remainder of the number in the destination floating-point data

#### register, using the source operand as the modulus. Stores the result in the destination

#### floating-point data register and stores the sign and seven least significant bits of the

#### quotient in the floating-point status register quotient byte (the quotient is the result of

#### FPn ÷ Source). The IEEE remainder function is defined as:

#### FPn – (Source x N)

#### where N = INT (FPn ÷ Source) in the round-to-nearest mode.

#### The FREM function is not defined for a source operand equal to zero or for a destina-

#### tion operand equal to infinity. Note that this function is not the same as the FMOD

#### instruction, which uses the round-to-zero mode and thus returns a remainder that is dif-

#### ferent from the remainder required by the IEEE Specification for Binary Floating-Point

#### Arithmetic.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.
3. Returns the value of FPn before the operation. However, the result is
    processed by the normal instruction termination procedure to round it as
    required. Thus, an overflow and/or inexact result may occur if the rounding
    precision has been changed to a smaller size since the FPn value was loaded.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero# – + Infinity –

```
In Range +
```
**-** IEEE Remainder NAN

(^2) FPn (^2)
**Zero +**

**-**

###### + 0.0

###### – 0.0 NAN

###### 2 + 0.0

###### – 0.0

```
Infinity +
```
**-** NAN

(^2) NAN (^2) NAN† 2


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-105

# FREM IEEE Remainder FREM

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Loaded with the sign and least significant seven bits of the

#### qotient (FPn ÷ Source). The sign of the quotient is the

#### exclusive-OR of the sign bits of the source and destination

#### operands.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is zero or the destination is

#### infinity; cleared otherwise.

#### OVFL Cleared

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0100101


##### Floating Point Instructions

##### 5-106 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FREM IEEE Remainder FREM

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-107

# FSCALE Scale Exponent FSCALE

#### (MC6888X, M68040FPSP)

#### Operation: FPn x INT(2Source) → FPn

#### Assembler FSCALE. < fmt > < ea > ,FPn

#### Syntax: FSCALE.X FPm,FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to an integer (if necessary) and adds that integer

#### to the destination exponent. Stores the result in the destination floating-point data

#### register. This function has the effect of multiplying the destination by 2Source, but is

#### much faster than a multiply operation when the source is an integer value.

#### The floating-point coprocessor assumes that the scale factor is an integer value before

#### the operation is executed. If not, the value is chopped (i.e., rounded using the round-

#### to-zero mode) to an integer before it is added to the exponent. When the absolute value

#### of the source operand is ≥ 214 , an overflow or underflow always results.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Returns the value of FPn before the operation. However, the result is
    processed by the normal instruction termination procedure to round it as
    required. Thus, an overflow and/or inexact result may occur if the rounding
    precision has been changed to a smaller size since the FPn value was
    loaded.
3. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

```
+ In Range – + Zero – + Infinity –
In Range + – Scale Exponent FPn^2 NAN^3
Zero + – + 0.0 – 0.0 + 0.0 – 0.0 NAN^3
Infinity + – + inf – inf + inf – inf NAN^3
```

##### Floating Point Instructions

##### 5-108 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSCALE Scale Exponent FSCALE

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source operand is ± infinity; cleared

#### otherwise.

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 1 0 0 1 1 0


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-109

# FSCALE Scale Exponent FSCALE

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-110 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FScc Set According to Floating-Point Condition FScc

#### (MC6888X, MC68040)

#### Operation: If (Condition True)

#### Then 1s → Destination

#### Else 0s → Destination

#### Assembler

#### Syntax: FScc. < size > < ea >

#### Attributes: Size = (Byte)

#### Description: If the specified floating-point condition is true, sets the byte integer operand at

#### the destination to TRUE (all ones); otherwise, sets the byte to FALSE (all zeros). The

#### conditional specifier cc may select any one of the 32 floating-point conditional tests as

#### described in Table 3-23 Floating-Point Conditional Tests.

#### Floating-Point Status Register:

#### Condition Codes: Not affected.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Set if the NAN condition code is set and the

#### condition selected is an IEEE nonaware test.

#### SNAN Not Affected.

#### OPERR Not Affected.

#### OVFL Not Affected.

#### UNFL Not Affected.

#### DZ Not Affected.

#### INEX2 Not Affected.

#### INEX1 Not Affected.

#### Accrued Exception Byte: The IOP bit is set if the BSUN bit is set in the exception

#### byte. No other bit is affected.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-111

# FScc Set According to Floating-Point Condition FScc

#### (MC6888X, MC68040)

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies the addressing mode for the byte integer operand.

#### Only data alterable addressing modes can be used as listed in the following table:

#### Conditional Predicate field—Specifies one of 32 conditional tests as defined in 3.6.2

#### Conditional Testing.

#### NOTE

#### When a BSUN exception occurs, a preinstruction exception is

#### taken. If the exception handler returns without modifying the im-

#### age of the program counter on the stack frame (to point to the

#### instruction following the FScc), then it must clear the cause of

#### the exception (by clearing the NAN bit or disabling the BSUN

#### trap) or the exception occurs again immediately upon return to

#### the routine that caused the exception.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^001) MODEEFFECTIVE ADDRESS REGISTER
0000000000 CONDITIONAL PREDICATE
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) — —


##### Floating Point Instructions

##### 5-112 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSGLDIV Single-Precision Divide FSGLDIV

#### (MC6888X, MC68040)

#### Operation: FPn ÷ Source → FPn

#### Assembler FSGLDIV. < fmt > < ea > ,FPn

#### Syntax: FSGLDIV.X FPm,FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and divides

#### that number into the number in the destination floating-point data register. Stores the

#### result in the destination floating-point data register, rounded to single precision (despite

#### the current rounding precision). This function is undefined for 0 ÷ 0 and infinity ÷ infinity.

#### Both the source and destination operands are assumed to be representable in the sin-

#### gle-precision format. If either operand requires more than 24 bits of mantissa to be

#### accurately represented, the extraneous mantissa bits are trancated prior to the divi-

#### sion, hence the accuracy of the result is not guaranteed. Furthermore, the result expo-

#### nent may exceed the range of single precision, regardless of the rounding precision

#### selected in the floating-point control register mode control byte. Refer to 3.6.1 Under-

#### flow, Round, Overflow for more information.

#### The accuracy of the result is not affected by the number of mantissa bits required to

#### represent each input operand since the input operands just change to extended preci-

#### sion. The result mantissa is rounded to single precision, and the result exponent is

#### rounded to extended precision, despite the rounding precision selected in the floating-

#### point control register.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the DZ bit in the floating-point status register exception byte.
3. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE3,1

##### + In Range – + Zero – + Infinity –

```
In Range +
```
**-**

```
Divide
(Single Precision)
```
```
+ inf^2 – inf^2
```
- inf^2 + inf^2

###### + 0.0– 0.0 – 0.0 + 0.0

```
Zero +
```
**-**

###### + 0.0 – 0.0 – 0.0+ 0.0 NAN 3 + 0.0 – 0.0

###### – 0.0 + 0.0

```
Infinity +
```
**-**

```
+ inf – inf – inf + inf+ inf – inf – inf + inf NAN 3
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-113

# FSGLDIV Single-Precision Divide FSGLDIV

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set for 0 ÷ 0 or infinity ÷ infinity.

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Set if the source is zero and the destination is

#### in range; cleared otherwise.

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to the appropriate

#### user’s manual for inexact result on decimal

#### input; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 1 0 0 1 0 0


##### Floating Point Instructions

##### 5-114 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSGLDIV Single-Precision Divide FSGLDIV

#### (MC6888X, MC68040)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-115

# FSGLMUL Single-Precision Multiply FSGLMUL

#### (MC6888X, MC68040)

#### Operation: Source x FPn → FPn

#### Assembler FSGLMUL. < fmt > < ea > ,FPn

#### Syntax: FSGLMUL.X FPm,FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### multiplies that number by the number in the destination floating-point data register.

#### Stores the result in the destination floating-point data register, rounded to single

#### precision (regardless of the current rounding precision).

#### Both the source and destination operands are assumed to be representable in the sin-

#### gle-precision format. If either operand requires more than 24 bits of mantissa to be

#### accurately represented, the extraneous mantissa bits are truncated prior to the multi-

#### pliction; hence, the accuracy of the result is not guaranteed. Furthermore, the result

#### exponent may exceed the range of single precision, regardless of the rounding preci-

#### sion selected in the floating-point control register mode control byte. Refer to 3.6.1

#### Underflow, Round, Overflow for more information.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

#### NOTE

#### The input operand mantissas truncate to single precision before

#### the multiply operation. The result mantissa rounds to single pre-

#### cision despite the rounding precision selected in the floating-

#### point control register.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
In Range +
```
**-**

```
Multiply
(Single Precision)
```
```
+ 0.0 – 0.0 + 0.0– 0.0 + inf – inf – inf + inf
```
```
Zero +
```
**-**

###### + 0.0– 0.0 – 0.0 + 0.0+ 0.0 – 0.0 – 0.0 + 0.0 NAN 2

```
Infinity +
```
**-**

```
+ inf – inf + inf– inf NAN + inf – inf – inf + inf
```

##### Floating Point Instructions

##### 5-116 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSGLMUL Single-Precision Multiply FSGLMUL

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if one operand is zero and the other is

#### infinity; cleared otherwise.

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0100111


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-117

# FSGLMUL Single-Precision Multiply FSGLMUL

#### (MC6888X, MC68040)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-118 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSIN Sine FSIN

#### (MC6888X, M68040FPSP)

#### Operation: Sine of Source → FPn

#### Assembler FSIN. < fmt > < ea > ,FPn

#### Syntax: FSIN.X FPm,FPn

#### FSIN.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the sine of that number. Stores the result in the destination floating-point

#### data register. This function is not defined for source operands of ± infinity. If the source

#### operand is not in the range of [ – 2π... + 2π], the argument is reduced to within that

#### range before the sine is calculated. However, large arguments may lose accuracy

#### during reduction, and very large arguments (greater than approximately 10^20 ) lose all

#### accuracy. The result is in the range of [ – 1... + 1].

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Sine + 0.0 – 0.0 NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-119

# FSIN Sine FSIN

#### (MC6888X, M68040FPSP)

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is ± infinity; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 1 1 1 0


##### Floating Point Instructions

##### 5-120 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSIN Sine FSIN

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, then the input operand is

#### taken from the specified floating-point data register, and the result is written into

#### the same register. If the single register syntax is used, Motorola assemblers set

#### the source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-121

# FSINCOS Simultaneous Sine and Cosine FSINCOS

#### (MC6888X, M68040FPSP)

#### Operation: Sine of Source → FPs

#### Cosine of Source → FPc

#### Assembler FSINCOS. < fmt > < ea > ,FPc,FPs

#### Syntax: FSINCOS.X FPm,FPc,FPs

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates both the sine and the cosine of that number. Calculates both functions

#### simultaneously; thus, this instruction is significantly faster than performing separate

#### FSIN and FCOS instructions. Loads the sine and cosine results into the destination

#### floating-point data register. Sets the condition code bits according to the sine result. If

#### FPs and FPc are specified to be the same register, the cosine result is first loaded into

#### the register and then is overwritten with the sine result. This function is not defined for

#### source operands of ± infinity.

#### If the source operand is not in the range of [ – 2π... + 2π], the argument is reduced to

#### within that range before the sine and cosine are calculated. However, large arguments

#### may lose accuracy during reduction, and very large arguments (greater than approxi-

#### mately 10^20 ) lose all accuracy. The results are in the range of [ – 1... + 1].

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
FPs Sine + 0.0 – 0.0 NAN^2
FPc Cosine + 1.0 NAN^2
```

##### Floating Point Instructions

##### 5-122 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSINCOS Simultaneous Sine and Cosine FSINCOS

#### (MC6888X, M68040FPSP)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing (for the

#### sine result).

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is ± infinity; cleared

#### otherwise.

#### OVFL Cleared

#### UNFL Set if a sine underflow occurs, in which case

#### the cosine result is 1. Cosine cannot

#### underflow. Refer to underflow in the

#### appropriate user’s manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE REGISTER, FPsDESTINATION (^0110) REGISTER FPc DESTINATION


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-123

# FSINCOS Simultaneous Sine and Cosine FSINCOS

#### (MC6888X, M68040FPSP)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register, FPc field—Specifies the destination floating- point data register,

#### FPc. The cosine result is stored in this register.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-124 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSINCOS Simultaneous Sine and Cosine FSINCOS

#### (MC6888X, M68040FPSP)

#### Destination Register, FPs field—Specifies the destination floating- point data register, FPs.

#### The sine result is stored in this register. If FPc and FPs specify the same floating-point

#### data register, the sine result is stored in the register, and the cosine result is discarded.

#### If R/M = 0 and the source register field is equal to either of the destination register

#### fields, the input operand is taken from the specified floating-point data register, and the

#### appropriate result is written into the same register.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-125

# FSINH Hyperbolic Sine FSINH

#### (MC6888X, M68040FPSP)

#### Operation: Hyperbolic Sine of Source → FPn

#### Assembler FSINH. < fmt > < ea > ,FPn

#### Syntax: FSINH.X FPm,FPn

#### FSINH.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the hyperbolic sine of that number. Stores the result in the destination

#### floating-point data register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result Hyperbolic Sine + 0.0 – 0.0 + inf – inf
```

##### Floating Point Instructions

##### 5-126 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSINH Hyperbolic Sine FSINH

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0000010
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-127

# FSINH Hyperbolic Sine FSINH

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, the input operand is taken

#### from the specified floating-point data register, and the result is written into the

#### same register. If the single register syntax is used, Motorola assemblers set the

#### source and destination fields to the same value.


##### Floating Point Instructions

##### 5-128 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSQRT Floating-Point Square Root FSQRT

#### (MC6888X, MC68040)

#### Operation: Square Root of Source → FPn

#### Assembler FSQRT. < fmt > < ea > ,FPn

#### Syntax: FSQRT.X FPm,FPn

#### FSQRT.X FPn

#### *FrSQRT. < fmt > < ea > ,FPn

#### *FrSQRT FPm,FPn

#### *FrSQRT FPn

#### where r is rounding precision, S or D

##### *Supported by MC68040 only

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the square root of that number. Stores the result in the destination floating-

#### point data register. This function is not defined for negative operands.

#### FSQRT will round the result to the precision selected in the floating-point control reg-

#### ister. FSFSQRT and FDFSQRT will round the result to single or double precision,

#### respectively, regardless of the rounding precision selected in the floating-point control

#### register.Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

#### Result x NAN^2 + 0.0 – 0.0+ inf NAN^2


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-129

# FSQRT Floating-Point Square Root FSQRT

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source operand is not zero and is

#### negative; cleared otherwise.

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE


##### Floating Point Instructions

##### 5-130 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSQRT Floating-Point Square Root FSQRT

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand. Only data addressing modes

#### can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding will cause an unimplemented data type exception in the

##### MC68040 to allow emulation in software.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-131

# FSQRT Floating-Point Square Root FSQRT

#### (MC6888X, MC68040)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, the input operand is taken

#### from the specified floating-point data register, and the result is written into the

#### same register. If the single register syntax is used, Motorola assemblers set the

#### source and destination fields to the same value.

#### Opmode field—Specifies the instruction and rounding precision.

#### 0000100 FSQRT Rounding precision specified by the floating-point

#### control register.

#### 1000001 FSSQRT Single-precision rounding specified.

#### 1000101 FDSQRT Double-precision rounding specified.


##### Floating Point Instructions

##### 5-132 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSUB Floating-Point Subtract FSUB

#### (MC6888X, MC68040)

#### Operation: FPn – Source → FPn

#### Assembler

#### Syntax: FSUB. < fmt > < ea > ,FPn

#### FSUB.X FPm,FPn

#### *FrSUB. < fmt > < ea > ,FPn

#### *FrSUB.X FPm,FPn

#### where r is rounding precision, S or D

##### *Supported by MC68040 only

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### subtracts that number from the number in the destination floating-point data register.

#### Stores the result in the destination floating-point data register.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Returns + 0.0 in rounding modes RN, RZ, and RP; returns – 0.0 in RM.
3. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
In Range +
```
**-** Subtract Subtract – inf + inf
**Zero +
-** Subtract

###### + 0.0^2 + 0.0

```
+ 0.0 + 0.0^2 – inf + inf
Infinity +
```
**-**

```
+ inf
```
- inf

```
+ inf
```
- inf

```
NAN^2 – inf
```
- inf NAN^2


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-133

# FSUB Floating-Point Subtract FSUB

#### (MC6888X, MC68040)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if both the source and destination are

#### like-signed infinities; cleared otherwise.

#### OVFL Refer to exception processing in the

#### appropriate user’s manual.

#### UNFL Refer to exception processing in the

#### appropriate user’s manual.

#### DZ Cleared

#### INEX2 Refer to exception processing in the

#### appropriate user’s manual.

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER OPMODE


##### Floating Point Instructions

##### 5-134 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSUB Floating-Point Subtract FSUB

#### (MC6888X, MC68040)

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand. Only data addressing modes

#### can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding will cause an unimplemented data type exception in the

##### MC68040 to allow emulation in software.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-135

# FSUB Floating-Point Subtract FSUB

#### (MC6888X, MC68040)

#### Destination Register field—Specifies the destination floating- point data register.

#### Opmode field—Specifies the instruction and rounding precision.

#### 0101000 FSUB Rounding precision specified by the floating- point

#### control register.

#### 1101000 FSSUB Single-precision rounding specified.

#### 1101100 FDSUB Double-precision rounding specified.


##### Floating Point Instructions

##### 5-136 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTAN Tangent FTAN

#### (MC6888X/004SW)

#### Operation: Tangent of Source → FPn

#### Assembler FTAN. < fmt > < ea > ,FPn

#### Syntax: FTAN.X FPm,FPn

#### FTAN.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the tangent of that number. Stores the result in the destination floating-point

#### data register. This function is not defined for source operands of ± infinity. If the source

#### operand is not in the range of [ – π/2... + π/2], the argument is reduced to within that

#### range before the tangent is calculated. However, large arguments may lose accuracy

#### during reduction, and very large arguments (greater than approximately 10^20 ) lose all

#### accuracy.

#### Operation Table:

###### NOTES:

1. If the source operand is a NAN, refer to **1.6.5 Not-A-Numbers** for more information.
2. Sets the OPERR bit in the floating-point status register exception byte.

##### DESTINATION

##### SOURCE^1

##### + In Range – + Zero – + Infinity –

```
Result Tangent + 0.0 – 0.0 NAN^2
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-137

# FTAN Tangent FTAN

#### (MC6888X/004SW)

#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Set if the source is ± infinity; cleared

#### otherwise.

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0001111


##### Floating Point Instructions

##### 5-138 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTAN Tangent FTAN

#### (MC6888X/004SW)

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, the input operand is taken

#### from the specified floating-point data register, and the result is written into the

#### same register. If the single register syntax is used, Motorola assemblers set the

#### source and destination fields to the same value.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-139

# FTANH Hyperbolic Tangent FTANH

#### (MC6888X, M68040FPSP)

#### Operation: Hyperbolic Tangent of Source → FPn

#### Assembler FTANH. < fmt > < ea > ,FPn

#### Syntax: FTANH.X FPm,FPn

#### FTANH.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates the hyperbolic tangent of that number. Stores the result in the destination

#### floating-point data register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION SOURCE

##### + In Range – + Zero – + Infinity –

```
Result Hyperbolic Tangent + 0.0 – 0.0 + 1.0 – 1.0
```

##### Floating Point Instructions

##### 5-140 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTANH Hyperbolic Tangent FTANH

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 0 1 0 0 1
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-141

# FTANH Hyperbolic Tangent FTANH

#### (MC6888X, M68040FPSP)

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, the input operand is taken

#### from the specified floating-point data register, and the result is written into the

#### same register. If the single register syntax is used, Motorola assemblers set the

#### source and destination fields to the same value.


##### Floating Point Instructions

##### 5-142 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTENTOX 10 x FTENTOX

#### (MC6888X, M68040FPSP)

#### Operation: 10 Source → FPn

#### Assembler FTENTOX. < fmt > < ea > ,FPn

#### Syntax: FTENTOX.X FPm,FPn

#### FTENTOX.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates 10 to the power of that number. Stores the result in the destination floating-

#### point data register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to the appropriate

#### user’s manual inexact result on decimal

#### input; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION SOURCE

##### + In Range – + Zero – + Infinity –

```
Result 10 x + 1.0 + inf + 0.0
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-143

# FTENTOX 10 x FTENTOX

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0 0 1 0 0 1 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-144 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTENTOX 10 x FTENTOX

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, the input operand is taken

#### from the specified floating-point data register, and the result is written into the

#### same register. If the single register syntax is used, Motorola assemblers set the

#### source and destination fields to the same value.


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-145

# FTRAPcc Trap on Floating-Point Condition FTRAPcc

#### (MC6888X, MC68040)

#### Operation: If Condition True

#### Then TRAP

#### Assembler FTRAPcc

#### Syntax: FTRAPcc.W # < data >

#### FTRAPcc.L # < data >

#### Attributes: Size = (Word, Long)

#### Description: If the selected condition is true, the processor initiates exception processing.

#### A vector number is generated to reference the TRAPcc exception vector. The stacked

#### program counter points to the next instruction. If the selected condition is not true, there

#### is no operation performed and execution continues with the next instruction in

#### sequence. The immediate data operand is placed in the word(s) following the

#### conditional predicate word and is available for user definition for use within the trap

#### handler.

#### The conditional specifier cc selects one of the 32 conditional tests defined in 3.6.2

#### Conditional Testing.

#### Floating-Point Status Register:

#### Condition Codes: Not affected.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Set if the NAN condition code is set and the

#### condition selected is an IEEE nonaware test.

#### SNAN Not Affected.

#### OPERR Not Affected.

#### OVFL Not Affected.

#### UNFL Not Affected.

#### DZ Not Affected.

#### INEX2 Not Affected.

#### INEX1 Not Affected.

#### Accrued Exception Byte: The IOP bit is set if the BSUN bit is set in the exception

#### byte; no other bit is affected.


##### Floating Point Instructions

##### 5-146 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTRAPcc Trap on Floating-Point Condition FTRAPcc

#### (MC6888X, MC68040)

#### Instruction Format:

#### Instruction Fields:

#### Mode field—Specifies the form of the instruction.

#### 010 — The instruction is followed by a word operand.

#### 011 — The instruction is followed by a long-word operand.

#### 100 — The instruction has no operand.

#### Conditional Predicate field—Specifies one of 32 conditional tests as described in 3.6.2

#### Conditional Testing.

#### Operand field—Contains an optional word or long-word operand that is user defined.

#### NOTE

#### When a BSUN exception occurs, a preinstruction exception is

#### taken by the main processor. If the exception handler returns

#### without modifying the image of the program counter on the stack

#### frame (to point to the instruction following the FTRAPcc), it must

#### clear the cause of the exception (by clearing the NAN bit or dis-

#### abling the BSUN trap), or the exception occurs again immediate-

#### ly upon return to the routine that caused the exception.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111 COPROCESSORID 001111 MODE
0000000000 CONDITIONAL PREDICATE
16-BIT OPERAND OR MOST SIGNIFICANT WORD OF 32-BIT OPERAND (IFNEEDED)
LEAST SIGNIFICANT WORD OR 32-BIT OPERAND (IF NEEDED)
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-147

# FTST Test Floating-Point Operand FTST

#### (MC6888X, MC68040)

#### Operation: Condition Codes for Operand → FPCC

#### Assembler FTST. < fmt > < ea >

#### Syntax: FTST.X FPm

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and sets the

#### condition code bits according to the data type of the result.

#### Operation Table: The contents of this table differfromtheother operation tables. A letter in

#### an entry of this table indicates that the designated condition code bit is always set by

#### the FTST operation. All unspecified condition code bits are cleared during the

#### operation.

```
NOTE: If the source operand is a NAN, set the NAN condition code bit. If the source
operand is an SNAN, set the SNAN bit in the floating-point status register
exception byte
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Cleared

#### UNFL Cleared

#### DZ Cleared

#### INEX2 Cleared

#### INEX1 If < fmt > is packed, refer to exception

#### processing in the appropriate user’s manual;

#### cleared otherwise.

#### Accrued Exception Byte: Affected as described in exception processing in the appro-

#### priate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result none N Z NZ I NI
```

##### Floating Point Instructions

##### 5-148 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTST Test Floating-Point Operand FTST

#### (MC6888X, MC68040)

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, specifies the location of the source operand. Only data addressing modes

#### can be used as listed in the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0111010
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-149

# FTST Test Floating-Point Operand FTST

#### (MC6888X, MC68040)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)*

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

##### *This encoding will cause an unimplemented data type exception in the

##### MC68040 to allow emulation in software.

#### Destination Register field—Since the floating-point unit uses a common command

#### word format for all of the arithmetic instructions (including FTST), this field is

#### treated in the same manner for FTST as for the other arithmetic instructions, even

#### though the destination register is not modified. This field should be set to zero to

#### maintain compatibility with future devices; however, the floating-point unit does

#### not signal an illegal instruction trap if it is not zero.


##### Floating Point Instructions

##### 5-150 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTWOTOX 2 x FTWOTOX

#### (MC6888X, M68040FPSP)

#### Operation: 2 Source → FPn

#### Assembler FTWOTOX. < fmt > < ea > ,FPn

#### Syntax: FTWOTOX.X FPm,FPn

#### FTWOTOX.X FPn

#### Attributes: Format = (Byte, Word, Long, Single, Double, Extended, Packed)

#### Description: Converts the source operand to extended precision (if necessary) and

#### calculates two to the power of that number. Stores the result in the destination floating-

#### point data register.

#### Operation Table:

```
NOTE: If the source operand is a NAN, refer to 1.6.5 Not-A-Numbers for more information.
```
#### Floating-Point Status Register:

#### Condition Codes: Affected as described in 3.6.2 Conditional Testing.

#### Quotient Byte: Not affected.

#### Exception Byte: BSUN Cleared

#### SNAN Refer to 1.6.5 Not-A-Numbers.

#### OPERR Cleared

#### OVFL Refer to overflow in the appropriate user’s

#### manual.

#### UNFL Refer to underflow in the appropriate user’s

#### manual.

#### DZ Cleared

#### INEX2 Refer to inexact result in the appropriate

#### user’s manual.

#### INEX1 If < fmt > is packed, refer to inexact result on

#### decimal input in the appropriate user’s

#### manual; cleared otherwise.

#### Accrued Exception Byte: Affected as described in IEEE exception and trap compati-

#### bility in the appropriate user’s manual.

##### DESTINATION

##### SOURCE

##### + In Range – + Zero – + Infinity –

```
Result 2 x + 1.0 + inf + 0.0
```

##### Floating Point Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 5-151

# FTWOTOX 2 x FTWOTOX

#### (MC6888X, M68040FPSP)

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Specifies which coprocessor in the system is to execute this

#### instruction. Motorola assemblers default to ID = 1 for the floating-point

#### coprocessor.

#### Effective Address field—Determines the addressing mode for external operands.

#### If R/M = 0, this field is unused and should be all zeros.

#### If R/M = 1, this field is encoded with an M68000 family addressing mode as listed in

#### the following table:

```
*Only if < fmt > is byte, word, long, or single.
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^000) MODEEFFECTIVE ADDRESS REGISTER
0 R/M (^0) SPECIFIERSOURCE DESTINATIONREGISTER 0010001
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn],od) 110 reg. number:An ([bd,PC,Xn],od) 111 011
([bd,An],Xn,od) 110 reg. number:An ([bd,PC],Xn,od) 111 011


##### Floating Point Instructions

##### 5-152 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FTWOTOX 2 x FTWOTOX

#### (MC6888X, M68040FPSP)

#### R/M field—Specifies the source operand address mode.

#### 0 — The operation is register to register.

#### 1 — The operation is < ea > to register.

#### Source Specifier field—Specifies the source register or data format.

#### If R/M = 0, specifies the source floating-point data register.

#### If R/M = 1, specifies the source data format:

#### 000 — Long-Word Integer (L)

#### 001 — Single-Precision Real (S)

#### 010 — Extended-Precision Real (X)

#### 011 — Packed-Decimal Real (P)

#### 100 — Word Integer (W)

#### 101 — Double-Precision Real (D)

#### 110 — Byte Integer (B)

#### Destination Register field—Specifies the destination floating- point data register. If R/

#### M = 0 and the source and destination fields are equal, the input operand is taken

#### from the specified floating-point data register, and the result is written into the

#### same register. If the single register syntax is used, Motorola assemblers set the

#### source and destination fields to the same value.


##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 6-1

## SECTION 6

## SUPERVISOR (PRIVILEGED) INSTRUCTIONS

#### This section contains information about the supervisor privileged instructions for the

#### M68000 family. Each instruction is described in detail, and the instruction descriptions are

#### arranged in alphabetical order by instruction mnemonic.

#### Any differences within the M68000 family of instructions are identified in the instruction. If an

#### instruction only applies to a certain processor or processors, the processor(s) that the

#### instruction pertains to is identified under the title of the instruction. For example:

### Invalidate Cache Lines

#### (MC68040)

#### All references to the MC68000, MC68020, and MC68030 include references to the

#### corresponding embedded controllers, MC68EC000, MC68EC020, and MC68EC030. All

#### references to the MC68040 include the MC68LC040 and MC68EC040. This applies

#### throughout this section unless otherwise specified.

#### If the instruction applies to all the M68000 family but a processor or processors may use a

#### different instruction field, instruction format, etc., the differences will be identified within the

#### paragraph. For example:

```
*Can be used with CPU32 processo
```
#### The following instructions are listed separately for each processor due to the many

#### differences involved within the instruction:

#### Appendix A Processor Instruction Summary

#### provides a listing of all processors and the

#### instructions that apply to them for quick reference.

##### MC68020, MC68030 and MC68040 only

```
(bd,An,Xn)* 110 reg. number: An (bd,PC,Xn)* — —
```
#### PFLUSH Flush ATC Entries

#### PMOVE Move PMMU Register

#### PTEST Test Logical Address


##### Supervisor (Privileged) Instructions

##### 6-2

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# ANDI ANDI

# to SR

## AND Immediate to the Status Register

# to SR

#### (M68000 Family)

#### Operation:

#### If Supervisor State

#### Then Source L SR

#### →

#### SR

#### ELSE TRAP

#### Assembler

#### Syntax:

#### ANDI # < data > ,SR

#### Attributes:

#### size = (word)

#### Description:

#### Performs an AND operation of the immediate operand with the contents of the

#### status register and stores the result in the status register. All implemented bits of the

#### status register are affected.

#### Condition Codes:

#### X—Cleared if bit 4 of immediate operand is zero; unchanged otherwise.

#### N—Cleared if bit 3 of immediate operand is zero; unchanged otherwise.

#### Z—Cleared if bit 2 of immediate operand is zero; unchanged otherwise.

#### V—Cleared if bit 1 of immediate operand is zero; unchanged otherwise.

#### C—Cleared if bit 0 of immediate operand is zero; unchanged otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
5 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 0 0 1 0 0 1 1 1 1 1 0 0
16-BIT WORD DATA
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 6-3

# CINV

## Invalidate Cache Lines

# CINV

#### (MC68040, MC68LC040)

#### Operation:

#### If Supervisor State

#### Then Invalidate Selected Cache Lines

#### ELSE TRAP

#### Assembler

#### Syntax:

#### CINVL < caches > ,(An)

#### CINVP < caches > ,(An)

#### CINVA < caches >

#### Where < caches > specifies the instruction cache,

#### data cache, both caches, or neither cache.

#### Attributes:

#### Unsized

#### Description:

#### Invalidates selected cache lines. The data cache, instruction cache, both

#### caches, or neither cache can be specified. Any dirty data in data cache lines that

#### invalidate are lost; the CPUSH instruction must be used when dirty data may be

#### contained in the data cache.

#### Specific cache lines can be selected in three ways:

#### 1. CINVL invalidates the cache line (if any) matching the physical address in the

#### specified address register.

#### 2. CINVP invalidates the cache lines (if any) matching the physical memory page

#### in the specified address register. For example, if 4K-byte page sizes are select-

#### ed and An contains $12345000, all cache lines matching page $12345000 in-

#### validate.

#### 3. CINVA invalidates all cache entries.

#### Condition Codes:

#### Not affected.


##### Supervisor (Privileged) Instructions

##### 6-4

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# CINV

## Invalidate Cache Lines

# CINV

#### (MC68040, MC68LC040)

#### Instruction Format:

#### Instruction Fields:

#### Cache field—Specifies the Cache.

#### 00—No Operation

#### 01—Data Cache

#### 10—Instruction Cache

#### 11—Data and Instruction Caches

#### Scope field—Specifies the Scope of the Operation.

#### 00—Illegal (causes illegal instruction trap)

#### 01—Line

#### 10—Page

#### 11—All

#### Register field—Specifies the address register for line and page operations. For line

#### operations, the low-order bits 3–0 of the address are don‘t cares. Bits 11–0 or 12–

#### 0 of the address are don‘t care for 4K-byte or 8K-byte page operations,

#### respectively.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
11110100 CACHE 0 SCOPE REGISTER
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 6-5

# cpRESTORE

## Coprocessor

# cpRESTORE

## Restore Functions

#### (MC68020, MC68030)

#### Operation:

#### If Supervisor State

#### Then Restore Internal State of Coprocessor

#### ELSE TRAP

#### Assembler

#### Syntax:

#### cpRESTORE < ea >

#### Attributes:

#### Unsized

#### Description:

#### Restores the internal state of a coprocessor usually after it has been saved by

#### a preceding cpSAVE instruction.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^101) MODEEFFECTIVE ADDRESS REGISTER


##### Supervisor (Privileged) Instructions

##### 6-6

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# cpRESTORE

## Coprocessor

# cpRESTORE

## Restore Functions

#### (MC68020, MC68030)

#### Instruction Fields:

#### Coprocessor ID field—Identifies the coprocessor that is to be restored. Coprocessor ID

#### of 000 results in an F-line exception for the MC68030.

#### Effective Address field—Specifies the location where the internal state of the

#### coprocessor is located. Only postincrement or control addressing modes can be

#### used as listed in the following table:

#### NOTE

#### If the format word returned by the coprocessor indicates “come

#### again”, pending interrupts are not serviced.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
— (An) — —
(d
16
,An) 101 reg. number:An (d
16
```
###### ,PC) 111 010

```
(d
8
,An,Xn) 110 reg. number:An (d
8
,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn], od) 110 reg. number:An ([bd,PC,Xn], od) 111 011
([bd,An],Xn,od) 110 reg.number:An ([bd,PC],Xn, od 111 011
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 6-7

# cpSAVE

## Coprocessor Save Function

# cpSAVE

#### (MC68020, MC68030)

#### Operation:

#### If Supervisor State

#### Then Save Internal State of Coprocessor

#### ELSE TRAP

#### Assembler

#### Syntax:

#### cpSAVE < ea >

#### Attributes:

#### Unsized

#### Description:

#### Saves the internal state of a coprocessor in a format that can be restored by

#### a cpRESTORE instruction.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Coprocessor ID field—Identifies the coprocessor for this operation. Coprocessor ID of

#### 000 results in an F-line exception for the MC68030.

#### Effective Address field—Specifies the location where the internal state of the

#### coprocessor is to be saved. Only predecrement or control alterable addressing

#### modes can be used as listed in the following table:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^100) MODEEFFECTIVE ADDRESS REGISTER
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
— (An) 100 reg. number:An
(d
16
,An) 101 reg. number:An (d
16

###### ,PC) — —

```
(d
8
,An,Xn) 110 reg. number:An (d
8
,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn], od) 110 reg. number:An ([bd,PC,Xn],od) — —
([bd,An],Xn, od) 110 reg. number:An ([bd,PC],Xn, od) — —
```

##### Supervisor (Privileged) Instructions

##### 6-8

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# CPUSH

## Push and Invalidate Cache Lines

# CPUSH

#### (MC68040, MC68LC040)

#### Operation:

#### If Supervisor State

#### Then If Data Cache

#### Then Push Selected Dirty Data Cache Lines

#### Invalidate Selected Cache Lines

#### ELSE TRAP

#### Assembler

#### CPUSHL < caches > ,(An)

#### Syntax:

#### CPUSHP < caches > ,(An)

#### CPUSHA < caches >

#### Where < caches > specifies the instruction cache, data cache,

#### both caches, or neither cache.

#### Attributes:

#### Unsized

#### Description:

#### Pushes and then invalidates selected cache lines. The DATA cache,

#### instruction cache, both caches, or neither cache can be specified. When the data cache

#### is specified, the selected data cache lines are first pushed to memory (if they contain

#### dirty DATA) and then invalidated. Selected instruction cache lines are invalidated.

#### Specific cache lines can be selected in three ways:

#### 1. CPUSHL pushes and invalidates the cache line (if any) matching the physical

#### address in the specified address register.

#### 2. CPUSHP pushes and invalidates the cache lines (if any) matching the physical

#### memory page in the specified address register. For example, if 4K-byte page

#### sizes are selected and An contains $12345000, all cache lines matching page

#### $12345000 are selected.

#### 3. CPUSHA pushes and invalidates all cache entries.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
11110100 CACHE 1 SCOPE REGISTER
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 6-9

# CPUSH

## Push and Invalidate Cache Lines

# CPUSH

#### (MC68040, MC68LC040)

#### Instruction Fields:

#### Cache field—Specifies the Cache.

#### 00—No Operation

#### 01—Data Cache

#### 10—Instruction Cache

#### 11—Data and Instruction Caches

#### Scope field—Specifies the Scope of the Operation.

#### 00—Illegal (causes illegal instruction trap)

#### 01—Line

#### 10—Page

#### 11—All

#### Register field—Specifies the address register for line and page operations. For line

#### operations, the low-order bits 3–0 of the address are don‘t care. Bits 11–0 or 12–

#### 0 of the address are don‘t care for 4K-byte or 8K-byte page operations,

#### respectively.


##### Supervisor (Privileged) Instructions

##### 6-10

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# EORI EORI

# to SR Exclusive-OR Immediate to the Status Register to SR

#### (M68000 Family)

#### Operation: If Supervisor State

#### Then Source ⊕ SR → SR

#### ELSE TRAP

#### Assembler

#### Syntax: EORI # < data > ,SR

#### Attributes: Size = (Word)

#### Description: Performs an exclusive-OR operation on the contents of the status register

#### using the immediate operand and stores the result in the status register. All

#### implemented bits of the status register are affected.

#### Condition Codes:

#### X—Changed if bit 4 of immediate operand is one; unchanged otherwise.

#### N—Changed if bit 3 of immediate operand is one; unchanged otherwise.

#### Z—Changed if bit 2 of immediate operand is one; unchanged otherwise.

#### V—Changed if bit 1 of immediate operand is one; unchanged otherwise.

#### C—Changed if bit 0 of immediate operand is one; unchanged otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 1 0 1 0 0 1 1 1 1 1 0 0
16-BIT WORD DATA
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-11

# FRESTORE Restore Internal FRESTORE

## Floating-Point State

#### (MC68881, MC68882, MC68040 only)

#### Operation: If in Supervisor State

#### Then FPU State Frame → Internal State

#### ELSE TRAP

#### Assembler

#### Syntax: FRESTORE < ea >

#### Attributes: Unsized

#### Description: Aborts the execution of any floating-point operation in progress and loads a

#### new floating-point unit internal state from the state frame located at the effective

#### address. The first word at the specified address is the format word of the state frame.

#### It specifies the size of the frame and the revision number of the floating-point unit that

#### created it. A format word is invalid if it does not recognize the size of the frame or the

#### revision number does not match the revision of the floating-point unit. If the format word

#### is invalid, FRESTORE aborts, and a format exception is generated. If the format word

#### is valid, the appropriate state frame is loaded, starting at the specified location and

#### proceeding through higher addresses.

#### The FRESTORE instruction does not normally affect the programmer’s model registers

#### of the floating-point coprocessor, except for the NULL state size, as described below.

#### It is only for restoring the user invisible portion of the machine. The FRESTORE

#### instruction is used with the FMOVEM instruction to perform a full context restoration of

#### the floating-point unit, including the floating- point data registers and system control

#### registers. To accomplish a complete restoration, the FMOVEM instructions are first

#### executed to load the programmer’s model, followed by the FRESTORE instruction to

#### load the internal state and continue any previously suspended operation.


##### Supervisor (Privileged) Instructions

##### 6-12 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FRESTORE Restore Internal FRESTORE

## Floating-Point State

#### (MC68881, MC68882, MC68040 only)

#### The current implementation supports the following four state frames:

#### NULL: This state frame is 4 bytes long, with a format word of $0000. An FRE-

#### STORE operation with this size state frame is equivalent to a hardware reset

#### of the floating-point unit. The programmer’s model is set to the reset state,

#### with nonsignaling NANs in the floating-point data registers and zeros in the

#### floating-point control register, floating-point status register, and floating-

#### point instruction address register. (Thus, it is unnecessary to load the pro-

#### grammer’s model before this operation.)

#### IDLE: This state frame is 4 bytes long in the MC68040, 28 ($1C) bytes long in the

#### MC68881, and 60 ($3C) bytes long in the MC68882. An FRESTORE oper-

#### ation with this state frame causes the floating-point unit to be restored to the

#### idle state, waiting for the initiation of the next instruction, with no exceptions

#### pending. The programmer’s model is not affected by loading this type of

#### state frame.

#### UNIMP: This state frame is generated only by the MC68040. It is 48 ($30) bytes long.

#### An FSAVE that generates this size frame indicates either an unimplemented

#### floating-point instruction or only an E1 exception is pending. This frame is

#### never generated when an unsupported data type exception is pending or an

#### E3 exception is pending. If both E1 and E3 exceptions are pending, a BUSY

#### frame is generated.

#### BUSY: This state frame is 96 ($60) bytes long in the MC68040, 184 ($B8) bytes long

#### in the MC68881, and 216 ($D8) bytes long in the MC68882. An FRESTORE

#### operation with this size state frame causes the floating-point unit to be

#### restored to the busy state, executing the instructions that were suspended

#### by a previous FSAVE operation. The programmer’s model is not affected by

#### loading this type of state frame; however, the completion of the suspended

#### instructions after the restore is executed may modify the programmer’s

#### model.

#### Floating-Point Status Register: Cleared if the state size is NULL; otherwise, not affected.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-13

# FRESTORE Restore Internal FRESTORE

## Floating-Point State

#### (MC68881, MC68882, MC68040 only)

#### Instruction Format:

#### Instruction Field:

#### Effective Address field—Determines the addressing mode for the state frame. Only

#### postincrement or control addressing modes can be used as listed in the following

#### table:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^101) MODEEFFECTIVE ADDRESS REGISTER
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn], od) 110 reg. number:An ([bd,PC,Xn], od) 111 011
([bd,An],Xn, od) 110 reg. number:An ([bd,PC],Xn, od) 111 011


##### Supervisor (Privileged) Instructions

##### 6-14 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSAVE Save Internal Floating-Point State FSAVE

#### (MC68881, MC68882, MC68040 only)

#### Operation: If in Supervisor State

#### Then FPU Internal State → State Frame

#### ELSE TRAP

#### Assembler

#### Syntax: FSAVE < ea >

#### Attributes: Unsized

#### Description: FSAVE allows the completion of any floating-point operation in progress for

#### the MC68040. It saves the internal state of the floating-point unit in a state frame

#### located at the effective address. After the save operation, the floating-point unit is in the

#### idle state, waiting for the execution of the next instruction. The first word written to the

#### state frame is the format word specifying the size of the frame and the revision number

#### of the floating-point unit.

#### Any floating-point operations in progress when an FSAVE instruction is encountered

#### can be completed before the FSAVE executes, saving an IDLE state frame. Execution

#### of instructions already in the floating-point unit pipeline continues until completion of all

#### instructions in the pipeline or generation of an exception by one of the instructions. An

#### IDLE state frame is created by the FSAVE if no exceptions occurred; otherwise, a

#### BUSY or an UNIMP stack frame is created.

#### FSAVE suspends the execution of any operation in progress and saves the internal

#### state in a state frame located at the effective address for the MC68881/MC68882. After

#### the save operation, the floating-point coprocessor is in the idle state, waiting for the

#### execution of the next instruction. The first word written to the state frame is the format

#### word, specifying the size of the frame and the revision number of the floating-point

#### coprocessor. The microprocessor unit initiates the FSAVE instruction by reading the

#### floating-point coprocessor save CIR. The floating-point coprocessor save CIR is

#### encoded with a format word that indicates the appropriate action to be taken by the

#### main processor. The current implementation of the floating-point coprocessor always

#### returns one of five responses in the save CIR:

```
NOTE: XX is the floating-point coprocessor version
number.
```
```
Value Definition
$0018 Save NULL state frame
$0118 Not ready, come again
$0218 Illegal, take format exception
$XX18 Save IDLE state frame
$XXB4 Save BUSY state frame
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-15

# FSAVE Save Internal Floating-Point State FSAVE

#### (MC68881, MC68882, MC68040 only)

#### The not ready format word indicates that the floating-point coprocessor is not prepared

#### to perform a state save and that the microprocessor unit should process interrupts, if

#### necessary, and re-read the save CIR. The floating-point coprocessor uses this format

#### word to cause the main processor to wait while an internal operation completes, if pos-

#### sible, to allow an IDLE frame rather than a BUSY frame to be saved. The illegal format

#### word aborts an FSAVE instruction that is attempted while the floating-point coproces-

#### sor executes a previous FSAVE instruction. All other format words cause the micropro-

#### cessor unit to save the indicated state frame at the specified address. For state frame

#### details see state frames in the appropriate user’s manual.

#### The following state frames apply to both the MC68040 and the MC68881/MC68882.

#### NULL: This state frame is 4 bytes long. An FSAVE instruction that generates this

#### state frame indicates that the floating-point unit state has not been modified

#### since the last hardware reset or FRESTORE instruction with a NULL state

#### frame. This indicates that the programmer’s model is in the reset state, with

#### nonsignaling NANs in the floating-point data registers and zeros in the float-

#### ing- point control register, floating-point status register, and floating-point

#### instruction address register. (Thus, it is not necessary to save the program-

#### mer’s model.)

#### IDLE: This state frame is 4 bytes long in the MC68040, 28 ($1C) bytes long in the

#### MC68881, and 60 ($3C) bytes long in the MC68882. An FSAVE instruction

#### that generates this state frame indicates that the floating-point unit finished

#### in an idle condition and is without any pending exceptions waiting for the ini-

#### tiation of the next instruction.

#### UNIMP: This state frame is generated only by the MC68040. It is 48 ($30) bytes long.

#### An FSAVE that generates this size frame indicates either an unimplemented

#### floating-point instruction or that only an E1 exception is pending. This frame

#### is never generated when an unsupported data type exception or an E3

#### exception is pending. If both E1 and E3 exceptions are pending, a BUSY

#### frame is generated.

#### BUSY: This state frame is 96 ($60) bytes long in the MC68040, 184 ($B8) bytes long

#### in the MC68881, and 216 ($D8) bytes long in the MC68882. An FSAVE

#### instruction that generates this size state frame indicates that the floating-

#### point unit encountered an exception while attempting to complete the execu-

#### tion of the previous floating-point instructions.


##### Supervisor (Privileged) Instructions

##### 6-16 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# FSAVE Save Internal Floating-Point State FSAVE

#### (MC68881, MC68882, MC68040 only)

#### The FSAVE does not save the programmer’s model registers of the floating-point unit;

#### it saves only the user invisible portion of the machine. The FSAVE instruction may be

#### used with the FMOVEM instruction to perform a full context save of the floating-point

#### unit that includes the floating-point data registers and system control registers. To

#### accomplish a complete context save, first execute an FSAVE instruction to suspend

#### the current operation and save the internal state, then execute the appropriate

#### FMOVEM instructions to store the programmer’s model.

#### Floating-Point Status Register: Not affected.

#### Instruction Format:

#### Instruction Field:

#### Effective Address field—Determines the addressing mode for the state frame. Only

#### predecrement or control alterable addressing modes can be used as listed in the

#### following table:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
1111 COPROCESSORID (^100) MODEEFFECTIVE ADDRESS REGISTER
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-17

# MOVE MOVE

# from SR Move from the Status Register from SR

#### (MC68EC000, MC68010, MC68020,

#### MC68030, MC68040, CPU32)

#### Operation: If Supervisor State

#### Then SR → Destination

#### Else TRAP

#### Assembler

#### Syntax: MOVE SR, < ea >

#### Attributes: Size = (Word)

#### Description: Moves the data in the status register to the destination location. The

#### destination is word length. Unimplemented bits are read as zeros.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100000011) MODEEFFECTIVE ADDRESS REGISTER


##### Supervisor (Privileged) Instructions

##### 6-18 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVE MOVE

# from SR Move from the Status Register from SR

#### (MC68EC000, MC68010, MC68020,

#### MC68030, MC68040, CPU32)

#### Instruction Field:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following tables:

```
*Available for the CPU32.
```
#### NOTE

#### Use the MOVE from CCR instruction to access only the

#### condition codes.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
```
##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-19

# MOVE MOVE

# to SR Move to the Status Register to SR

#### (M68000 Family)

#### Operation: If Supervisor State

#### Then Source → SR

#### Else TRAP

#### Assembler

#### Syntax: MOVE < ea > ,SR

#### Attributes: Size = (Word)

#### Description: Moves the data in the source operand to the status register. The source

#### operand is a word, and all implemented bits of the status register are affected.

#### Condition Codes:

#### Set according to the source operand.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^0100011011) MODEEFFECTIVE ADDRESS REGISTER


##### Supervisor (Privileged) Instructions

##### 6-20 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVE MOVE

# to SR Move to the Status Register to SR

#### (M68000 Family)

#### Instruction Field:

#### Effective Address field—Specifies the location of the source operand. Only data

#### addressing modes can be used as listed in the following tables:

```
*Available for the CPU32.
```
```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
```
##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* 111 011
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) 111 011
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) 111 011
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-21

# MOVE MOVE

# USP Move User Stack Pointer USP

#### (M68000 Family)

#### Operation: If Supervisor State

#### Then USP → An or An → USP

#### Else TRAP

#### Assembler MOVE USP,An

#### Syntax: MOVE An,USP

#### Attributes: Size = (Long)

#### Description: Moves the contents of the user stack pointer to or from the specified address

#### register.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### dr field—Specifies the direction of transfer.

#### 0—Transfer the address register to the user stack pointer.

#### 1—Transfer the user stack pointer to the address register.

#### Register field—Specifies the address register for the operation.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 0 dr REGISTER
```

##### Supervisor (Privileged) Instructions

##### 6-22 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVEC Move Control Register MOVEC

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### Operation: If Supervisor State

#### Then Rc → Rn or Rn → Rc

#### Else TRAP

#### Assembler MOVEC Rc,Rn

#### Syntax: MOVEC Rn,Rc

#### Attributes: Size = (Long)

#### Description: Moves the contents of the specified control register (Rc) to the specified

#### general register (Rn) or copies the contents of the specified general register to the

#### specified control register. This is always a 32-bit transfer, even though the control

#### register may be implemented with fewer bits. Unimplemented bits are read as zeros.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

#### Instruction Fields:

#### dr field—Specifies the direction of the transfer.

#### 0—Control register to general register.

#### 1—General register to control register.

#### A/D field—Specifies the type of general register.

#### 0—Data Register

#### 1—Address Rregister

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 1 0 1 dr
A/D REGISTER CONTROL REGISTER
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-23

# MOVEC Move Control Register MOVEC

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### Register field—Specifies the register number.

#### Control Register field—Specifies the control register.

###### NOTES:

1. Any other code causes an illegal instruction exception
2. For the MC68020 and MC68030 only.

```
Hex^1 Control Register
MC68010/MC68020/MC68030/MC68040/CPU32
000 Source Function Code (SFC)
001 Destination Function Code (DFC)
800 User Stack Pointer (USP)
801 Vector Base Register (VBR)
```
##### MC68020/MC68030/MC68040

```
002 Cache Control Register (CACR)
802 Cache Address Register (CAAR)^2
803 Master Stack Pointer (MSP)
804 Interrupt Stack Pointer (ISP)
```
##### MC68040/MC68LC040

```
003 MMU Translation Control Register (TC)
004 Instruction Transparent Translation Register 0 (ITT0)
005 Instruction Transparent Translation Register 1 (ITT1)
006 Data Transparent Translation Register 0 (DTT0)
007 Data Transparent Translation Register 1 (DTT1)
805 MMU Status Register (MMUSR)
806 User Root Pointer (URP)
807 Supervisor Root Pointer (SRP)
```
##### MC68EC040 only

```
004 Instruction Access Control Register 0 (IACR0)
005 Instruction Access Control Register 1 (IACR1)
006 Data Access Control Register 0 (DACR1)
007 Data Access Control Register 1 (DACR1)
```

##### Supervisor (Privileged) Instructions

##### 6-24 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVES Move Address Space MOVES

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### Operation: If Supervisor State

#### Then Rn → Destination [DFC] or Source [SFC] → Rn

#### Else TRAP

#### Assembler MOVES Rn, < ea >

#### Syntax: MOVES < ea > ,Rn

#### Attributes: Size = (Byte, Word, Long)

#### Description: This instruction moves the byte, word, or long operand from the specified

#### general register to a location within the address space specified by the destination

#### function code (DFC) register, or it moves the byte, word, or long operand from a

#### location within the address space specified by the source function code (SFC) register

#### to the specified general register. If the destination is a data register, the source operand

#### replaces the corresponding low-order bits of that data register, depending on the size

#### of the operation. If the destination is an address register, the source operand is sign-

#### extended to 32 bits and then loaded into that address register.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
00001110 SIZE MODEEFFECTIVE ADDRESS REGISTER
A/D REGISTER dr 0 0 0 0 0 0 0 0 0 0 0
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-25

# MOVES Move Address Space MOVES

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### Instruction Fields:

#### Size field—Specifies the size of the operation.

#### 00—Byte Operation

#### 01—Word Operation

#### 10—Long Operation

#### Effective Address field—Specifies the source or destination location within the alternate

#### address space. Only memory alterable addressing modes can be used as listed in

#### the following tables:

```
*Available for the CPU32.
```
#### A/D field—Specifies the type of general register.

#### 0—Data Register

#### 1—Address Register

#### Register field—Specifies the register number.

#### dr field—Specifies the direction of the transfer.

#### 0—From < ea > to general register.

#### 1—From general register to < ea >.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
```
##### MC68020, MC68030, and MC68040 only

```
(bd,An,Xn)* 110 reg. number:An (bd,PC,Xn)* — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —
```

##### Supervisor (Privileged) Instructions

##### 6-26 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# MOVES Move Address Space MOVES

#### (MC68010, MC68020, MC68030, MC68040, CPU32)

#### NOTE

#### The value stored is undefined for either of the two following

#### examples with the same address register as both source and

#### destination.

#### MOVES.x An,(An) +

#### MOVES.x An,D(An)

#### The current implementations of the MC68010, MC68020,

#### MC68030, and MC68040 store the incremented or decremented

#### value of An. Check the following code sequence to determine

#### what value is stored for each case.

#### MOVEA.L #$1000,A0

#### MOVES.L A0,(A0) +

#### MOVES.L A0,D(A0)

#### Because the MC68040 implements a merged instruction and

#### data space, the MC68040’s integer unit into data references

#### (SFC/DFC = 5 or 1) translates MOVES accesses to the

#### OinstructionO address spaces (SFC/DFC = 6 or 2). The data

#### memory unit handles these translated accesses as normal data

#### accesses. If the access fails due to an ATC fault or a physical

#### bus error, the resulting access error stack frame contains the

#### converted function code in the TM field for the faulted access. To

#### maintain cache coherency, MOVES accesses to write the

#### OinstructionO address space must be preceded by invalidation

#### of the instruction cache line containing the referenced location.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-27

# ORI ORI

# to SR Inclusive-OR Immediate to the Status Register to SR

#### (M68000 Family)

#### Operation: If Supervisor State

#### Then Source V SR → SR

#### Else TRAP

#### Assembler

#### Syntax: ORI # < data > ,SR

#### Attributes: Size = (Word)

#### Description: Performs an inclusive-OR operation of the immediate operand and the status

#### register’s contents and stores the result in the status register. All implemented bits of

#### the status register are affected.

#### Condition Codes:

#### X—Set if bit 4 of immediate operand is one; unchanged otherwise.

#### N—Set if bit 3 of immediate operand is one; unchanged otherwise.

#### Z—Set if bit 2 of immediate operand is one; unchanged otherwise.

#### V—Set if bit 1 of immediate operand is one; unchanged otherwise.

#### C—Set if bit 0 of immediate operand is one; unchanged otherwise.

#### Instruction Format:

###### X N Z V C

###### ∗∗∗∗∗

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 0 0 0 0 0 0 0 0 1 1 1 1 1 0 0
16—BIT WORD DATA
```

##### Supervisor (Privileged) Instructions

##### 6-28 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PBcc Branch on PMMU Condition PBcc

#### (MC68851)

#### Operation: If Supervisor State

#### Then If cc True

#### Then (PC) + dn → PC

#### Else TRAP

#### Assembler

#### Syntax: PBcc. < size > < label >

#### Attributes: Size = (Word, Long)

#### Description: If the specified paged memory management unit condition is met, execution

#### continues at location (PC) + displacement. The displacement is a twos complement

#### integer that counts the relative distance in bytes. The value in the program counter is

#### the address of the displacement word(s). The displacement may be either 16 or 32 bits.

#### The condition specifier cc indicates the following conditions:

#### PMMU Status Register: Not affected.

#### Instruction Format:

```
Specifier Description Condition Field Specifier Description Condition Field
BS B set 000000 BC B clear 000001
LS L set 000010 LC L clear 000011
SS S set 000100 SC S clear 000101
AS A set 000110 AC A clear 000111
WS W set 001000 WC W clear 001001
IS I set 001010 IC I clear 001011
GS G set 001100 GC G clear 001101
CS C set 001110 CC C clear 001111
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
111100001 SIZE MC68851 CONDITION
16-BIT DISPLACEMENT OR MOST SIGNIFICANT WORD OF 32-BITDISPLACEMENT
LEAST SIGNIFICANT WORD OF 32-BIT DISPLACEMENT (IF NEEDED)
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-29

# PBcc Branch on PMMU Condition PBcc

#### (MC68851)

#### Instruction Fields:

#### Size field—Specifies the size of the displacement.

#### 0—Displacement is 16 bits.

#### 1—Displacement is 32 bits.

#### MC68851 Condition field—Specifies the coprocessor condition to be tested. This field

#### is passed to the MC68851, which provides directives to the main processor for

#### processing this instruction.

#### Word Displacement field—The shortest displacement form for MC68851 branches is

#### 16 bits.

#### Long-Word Displacement field—Allows a displacement larger than 16 bits.


##### Supervisor (Privileged) Instructions

##### 6-30 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PDBcc Test, Decrement, and Branch PDBcc

#### (MC68851)

#### Operation: If Supervisor State

#### Then If cc False

#### Then (DnD1 → Dn; If Dn < > D1 then (PC) + d 3 PC)

#### Else No Operation

#### Else TRAP

#### Assembler

#### Syntax: PDBcc Dn, < label >

#### Attributes: Size = (Word)

#### Description: This instruction is a looping primitive of three parameters: an MC68851

#### condition, a counter (an MC68020 data register), and a 16-bit displacement. The

#### instruction first tests the condition to determine if the termination condition for the loop

#### has been met. If so, the main processor executes the next instruction in the instruction

#### stream. If the termination condition is not true, the low-order 16 bits of the counter

#### register are decremented by one. If the result is not D1, execution continues at the

#### location specified by the current value of the program counter plus the sign-extended

#### 16-bit displacement. The value of the program counter used in the branch address

#### calculation is the address of the PDBcc instruction plus two.

#### The condition specifier cc indicates the following conditions:

```
Specifier Description Condition Field Specifier Description Condition Field
BS B set 000000 BC B clear 000001
LS L set 000010 LC L clear 000011
SS S set 000100 SC S clear 000101
AS A set 000110 AC A clear 000111
WS W set 001000 WC W clear 001001
IS I set 001010 IC I clear 001011
GS G set 001100 GC G clear 001101
CS C set 001110 CC C clear 001111
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-31

# PDBcc Test, Decrement, and Branch PDBcc

#### (MC68851)

#### PMMU Status Register: Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Register field—Specifies the data register in the main processor to be used as the

#### counter.

#### MC68851 Condition field—Specifies the MC68851 condition to be tested. This field is

#### passed to the MC68851, which provides directives to the main processor for

#### processing this instruction.

#### Displacement field—Specifies the distance of the branch in bytes.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111000001001 COUNT REGISTER
0000000000 MC68851 CONDITION
16-BIT DISPLACEMENT
```

##### Supervisor (Privileged) Instructions

##### 6-32 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PFLUSH Flush Entry in the ATC PFLUSH

#### (MC68030 only)

#### Operation: If Supervisor State

#### Then Invalidate ATC Entries for Destination Addresses

#### Else TRAP

#### Assembler PFLUSHA

#### Syntax: PFLUSH FC,MASK

#### PFLUSH FC,MASK, < ea >

#### Attributes: Unsized

#### Description: PFLUSH invalidates address translation cache entries. The instruction has

#### three forms. The PFLUSHA instruction invalidates all entries. When the instruction

#### specifies a function code and mask, the instruction invalidates all entries for a selected

#### function code(s). When the instruction also specifies an < ea > , the instruction

#### invalidates the page descriptor for that effective address entry in each selected function

#### code.

#### The mask operand contains three bits that correspond to the three function code bits.

#### Each bit in the mask that is set to one indicates that the corresponding bit of the FC

#### operand applies to the operation. Each bit in the mask that is zero indicates a bit of FC

#### and of the ignored function code. For example, a mask operand of 100 causes the

#### instruction to consider only the most significant bit of the FC operand. If the FC operand

#### is 001, function codes 000, 001, 010, and 011 are selected.

#### The FC operand is specified in one of the following ways:

#### 1. Immediate—Three bits in the command word.

#### 2. Data Register—The three least significant bits of the data register specified in

#### the instruction.

#### 3. Source Function Code (SFC) Register

#### 4. Destination Function Code (DFC) Register

#### Condition Codes:

#### Not affected.

#### MMU Status Register:

#### Not affected.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-33

# PFLUSH Flush Entry in the ATC PFLUSH

#### (MC68030 only)

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies a control alterable address. The address translation

#### cache entry for this address is invalidated. Valid addressing modes are in the

#### following table:

#### NOTE

#### The address field must provide the memory management unit

#### with the effective address to be flushed from the address

#### translation cache, not the effective address describing where the

#### PFLUSH operand is located. For example, to flush the address

#### translation cache entry corresponding to a logical address that

#### is temporarily stored on top of the system stack, the instruction

#### PFLUSH [(SP)] must be used since PFLUSH (SP) would

#### invalidate the address translation cache entry mapping the

#### system stack (i.e., the effective address passed to the memory

#### management unit is the effective address of the system stack,

#### not the effective address formed by the operand located on the

#### top of the stack).

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 0 1 MODE 0 0 MASK FC
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### 6-34 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PFLUSH Flush Entry in the ATC PFLUSH

#### (MC68030 only)

#### Mode field—Specifies the type of flush operation.

#### 001—Flush all entries.

#### 100—Flush by function code only.

#### 110—Flush by function code and effective address.

#### Mask field—Mask for selecting function codes. Ones in the mask correspond to

#### applicable bits; zeros are bits to be ignored. When mode is 001, mask must be

#### 000.

#### FC field—Function code of entries to be flushed. If the mode field is 001, FC field must

#### be 00000; otherwise:

#### 10XXX — Function code is specified as bits XXX.

#### 01DDD — Function code is specified as bits 2–0 of data register DDD.

#### 00000 — Function code is specified as SFC register.

#### 00001 — Function code is specified as DFC register.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-35

# PFLUSH Flush ATC Entries PFLUSH

#### (MC68040, MC68LC040)

#### Operation: If Supervisor State

#### Then Invalidate Instruction and Data ATC Entries for Destination

#### Address

#### Else TRAP

#### Assembler PFLUSH (An)

#### Syntax: PFLUSHN (An)

#### Syntax: PFLUSHA

#### Syntax: PFLUSHAN

#### Attributes: Unsized

#### Description: Invalidates address translation cache entries in both the instruction and data

#### address translation caches. The instruction has two forms. The PFLUSHA instruction

#### invalidates all entries. The PFLUSH (An) instruction invalidates the entry in each

#### address translation cache which matches the logical address in An and the specified

#### function code.

#### The function code for PFLUSH is specified in the destination function code register.

#### Destination function code values of 1 or 2 will result in flushing of user address trans-

#### lation cache entries in both address translation caches; whereas, values of 5 or 6 will

#### result in flushing of supervisor address translation cache entries. PFLUSH is undefined

#### for destination function code values of 0, 3, 4, and 7 and may cause flushing of an

#### unexpected entry.

#### The PFLUSHN and PFLUSHAN instructions have a global option specified and invali-

#### date only nonglobal entries. For example, if only page descriptors for operating system

#### code have the global bit set, these two PFLUSH variants can be used to flush only user

#### address translation cache entries during task swaps.

#### Condition Codes:

#### Not affected.


##### Supervisor (Privileged) Instructions

##### 6-36 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PFLUSH Flush ATC Entries PFLUSH

#### (MC68040, MC68LC040)

#### Instruction Format:

##### Postincrement Source and Destination

#### Instruction Fields:

#### Opmode field—Specifies the flush operation.

#### Register field—Specifies the address register containing the effective address to be

#### flushed when flushing a page entry.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
11110101000 OPMODE REGISTER
```
```
Opcode Operation Assembler Syntax
00 Flush page entry if not global PFLUSHN (An)
01 Flush page entry PFLUSH (An)
10 Flush all except global entries PFLUSHAN
11 Flush all entries PFLUSHA
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-37

# PFLUSH Flush ATC Entries PFLUSH

#### (MC68EC040)

#### Operation: If Supervisor State

#### Then No Operation

#### Else TRAP

#### Assembler PFLUSH (An)

#### Syntax: PFLUSHN (An)

#### Attributes: Unsized

#### Description: This instruction should not be executed when using an MC68EC040. The

#### PFLUSH encoding suspends operation of the MC68EC040 for an indefinite period of

#### time and subsequently continues with no adverse effects.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

##### Postincrement Source and Destination

#### Instruction Fields:

#### Opmode field—Specifies the flush operation.

#### Register field—Specifies the address register containing the effective address to be

#### flushed when flushing a page entry.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
11110101000 OPMODE REGISTER
```
```
Opcode Operation Assembler Syntax
00 Flush page entry if not global PFLUSHN (An)
01 Flush page entry PFLUSH (An)
10 Flush all except global entries PFLUSHAN
11 Flush all entries PFLUSHA
```

##### Supervisor (Privileged) Instructions

##### 6-38 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PFLUSH PFLUSH

# PFLUSHA PFLUSHA

# PFLUSHS Invalidate Entries in the ATC PFLUSHS

#### (MC68851)

#### Operation: If Supervisor State

#### Then Address Translation Cache Entries For Destination Address

#### Are Invalidated

#### Else TRAP

#### Assembler PFLUSHA

#### Syntax: PFLUSH FC,MASK

#### PFLUSHS FC,MASK

#### PFLUSH FC,MASK, < ea >

#### PFLUSHS FC,MASK, < ea >

#### Attributes: Unsigned

#### Description: PFLUSHA invalidates all entries in the address translation cache.

#### PFLUSH invalidates a set of address translation cache entries whose function code

#### bits satisfy the relation: (address translation cache function code bits and mask) = (FC

#### and MASK) for all entries whose task alias matches the task alias currently active when

#### the instruction is executed. With an additional effective address argument, PFLUSH

#### invalidates a set of address translation cache entries whose function code satisfies the

#### relation above and whose effective address field matches the corresponding bits of the

#### evaluated effective address argument. In both of these cases, address translation

#### cache entries whose SG bit is set will not be invalidated unless the PFLUSHS is spec-

#### ified.

#### The function code for this operation may be specified as follows:

#### 1. Immediate—The function code is four bits in the command word.

#### 2. Data Register—The function code is in the lower four bits of the MC68020 data

#### register specified in the instruction.

#### 3. Source Function Code (SFC) Register—The function code is in the CPU SFC

#### register. Since the SFC of the MC68020 has only three implemented bits, only

#### function codes $0D$7 can be specified in this manner.

#### 4. Destination Function Code (DFC) Register—The function code is in the CPU

#### DFC register. Since the DFC of the MC68020 has only three implemented bits,

#### only function codes $0D$7 can be specified in this manner.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-39

# PFLUSH PFLUSH

# PFLUSHA PFLUSHA

# PFLUSHS Invalidate Entries in the ATC PFLUSHS

#### (MC68851)

#### PMMU Status Register: Not affected.

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies an address whose page descriptor is to be flushed

#### from (invalidated) the address translation cache. Only control alterable addressing

#### modes can be used as listed in the following table:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 0 1 MODE 0 MASK FC
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### 6-40 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PFLUSH PFLUSH

# PFLUSHA PFLUSHA

# PFLUSHS Invalidate Entries in the ATC PFLUSHS

#### (MC68851)

#### NOTE

#### The effective address field must provide the MC68851 with the

#### effective address of the entry to be flushed from the address

#### translation cache, not the effective address describing where the

#### PFLUSH operand is located. For example, in order to flush the

#### address translation cache entry corresponding to a logical

#### address that is temporarily stored on the top of the system stack,

#### the instruction PFLUSH [(SP)] must be used since PFLUSH

#### (SP) would invalidate the address translation cache entry

#### mapping the system stack (i.e., the effective address passed to

#### the MC68851 is the effective address of the system stack, not

#### the effective address formed by the operand located on the top

#### of the stack).

#### Mode field—Specifies how the address translation cache is to be flushed.

#### 001—Flush all entries.

#### 100—Flush by function code only.

#### 101—Flush by function code including shared entries.

#### 110—Flush by function code and effective address.

#### 111—Flush by function code and effective address including shared entries.

#### Mask field—Indicates which bits are significant in the function code compare. A zero

#### indicates that the bit position is not significant; a one indicates that the bit position

#### is significant. If mode = 001 (flush all entries), mask must be 0000.

#### FC field—Function code of address to be flushed. If the mode field is 001 (flush all

#### entries), function code must be 00000; otherwise:

#### 1DDDD — Function code is specified as four bits DDDD.

#### 01RRR — Function code is contained in CPU data register RRR.

#### 00000 — Function code is contained in CPU SFC register.

#### 00001 — Function code is contained in CPU DFC register.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-41

# PFLUSHR Invalidate ATC and RPT Entries PFLUSHR

#### (MC68851)

#### Operation: If Supervisor State

#### Then RPT Entry (If Any) Matching Root Pointer Specified by < ea >

#### Corresponding Address Translation Cache Entries Are Invalidated

#### Else TRAP

#### Assembler

#### Syntax: PFLUSHR < ea >

#### Attributes: Unsized

#### Description: The quad word pointed to by < ea > is regarded as a previously used value of

#### the CPU root pointer register. The root pointer table entry matching this CPU root

#### pointer register (if any) is flushed, and all address translation cache entries loaded with

#### this value of CPU root pointer register (except for those that are globally shared) are

#### invalidated. If no entry in the root pointer table matches the operand of this instruction,

#### no action is taken.

#### If the supervisor root pointer is not in use, the operating system should not issue the

#### PFLUSHR command to destroy a task identified by the current CPU root pointer reg-

#### ister. It should wait until the CPU root pointer register has been loaded with the root

#### pointer identifying the next task until using the PFLUSHR instruction. At any time, exe-

#### cution of the PFLUSHR instruction for the current CPU root pointer register causes the

#### current task alias to be corrupted.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
1 0 1 0 0 0 0 0 0 0 0 0 0 0 0 0


##### Supervisor (Privileged) Instructions

##### 6-42 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PFLUSHR Invalidate ATC and RPT Entries PFLUSHR

#### (MC68851)

#### Instruction Field:

#### Effective Address field—Specifies the address of a previous value of the CPU root

#### pointer register register. Only memory addressing modes can be used as listed in

#### the following table:

#### NOTE

#### The effective address usage of this instruction is different than

#### that of other PFLUSH variants.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) 111 011
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) 111 011
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-43

# PLOAD Load an Entry into the ATC PLOAD

#### (MC68030 only, MC68851)

#### Operation: If Supervisor State

#### Then Search Translation Table and Make Address Translation

#### Cache Entry for Effective Address

#### Else TRAP

#### Assembler PLOADR FC, < ea >

#### Syntax: PLOADW FC, < ea >

#### Attributes: Unsized

#### Description: For the MC68851, PLOAD searches the translation table for a translation of

#### the specified effective address. If one is found, it is flushed from the address translation

#### cache, and an entry is made as if a bus master had run a bus cycle. Used and modified

#### bits in the table are updated as part of the table search. The MC68851 ignores the

#### logical bus arbitration signals during the flush and load phases at the end of this

#### instruction. This prevents the possibility of an entry temporarily disappearing from the

#### address translation cache and causing a false table search.

#### This instruction will cause a paged memory management unit illegal operation excep-

#### tion (vector $39) if the E-bit of the translation control register is clear.

#### The function code for this operation may be specified to be:

#### 1. Immediate—The function code is specified as four bits in the command word.

#### 2. Data Register—The function code is contained in the lower four bits in the

#### MC68020 data register specified in the instruction.

#### 3. Source Function Code (SFC) Register—The function code is in the CPU SFC

#### register. Since the SFC of the MC68020 has only three implemented bits, only

#### function codes $0D$7 can be specified in this manner.

#### 4. Destination Function Code (DFC) Register—The function code is in the CPU

#### DFC register. Since the DFC of the MC68020 has only three implemented bits,

#### only function codes $0D$7 can be specified in this manner.


##### Supervisor (Privileged) Instructions

##### 6-44 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PLOAD Load an Entry into the ATC PLOAD

#### (MC68030 only, MC68851)

#### For the MC68030, PLOAD searches the address translation cache for the specified

#### effective address. It also searches the translation table for the descriptor corresponding

#### to the specified effective address. It creates a new entry as if the MC68030 had

#### attempted to access that address. Sets the used and modified bits appropriately as part

#### of the search. The instruction executes despite the value of the E-bit in the translation

#### control register or the state of the MMUDIS signal.

#### The < function code > operand is specified in one of the following ways:

#### 1. Immediate—Three bits in the command word.

#### 2. Data Register—The three least significant bits of the data register specified in

#### the instruction.

#### 3. Source Function Code (SFC) Register

#### 4. Destination Function Code (DFC) Register

#### The effective address field specifies the logical address whose translation is to be

#### loaded.

#### PLOADR causes U bits in the translation tables to be updated as if a read access had

#### occurred. PLOADW causes U and M bits in the translation tables to be updated as if a

#### write access had occurred.

#### PMMU Status Register: Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 0 1 0 0 0 R/ W 0 0 0 0 FC


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-45

# PLOAD Load an Entry into the ATC PLOAD

#### (MC68030 only, MC68851)

#### Instruction Fields:

#### Effective Address field—Specifies the logical address whose translation is to be loaded

#### into the address translation cache. Only control alterable addressing modes are

#### allowed as listed in the following table:

#### NOTE

#### The effective address field must provide the MC68851 with the

#### effective address of the entry to be loaded into the address

#### translation cache, not the effective address describing where the

#### PLOAD operand is located. For example, to load an address

#### translation cache entry to map a logical address that is

#### temporarily stored on the system stack, the instruction PLOAD

#### [(SP)] must be used since PLOAD (SP) would load an address

#### translation cache entry mapping the system stack (i.e., the

#### effective address passed to the MC68851 is the effective

#### address of the system stack, not the effective address formed by

#### the operand located on the top of the stack).

#### R/W field—Specifies whether the tables should be updated for a read or a write.

#### 1—Read

#### 0—Write

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —
```

##### Supervisor (Privileged) Instructions

##### 6-46 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PLOAD Load an Entry into the ATC PLOAD

#### (MC68030 only, MC68851)

#### FC field (MC68851)—Function code of address to load.

#### 1DDDD — Function code is specified as four bits DDDD.

#### 01RRR — Function code is contained in CPU data register RRR.

#### 00000 — Function code is contained in CPU SFC register.

#### 00001 — Function code is contained in CPU DFC register.

#### FC field (MC68030)—Function code of address corresponding to entry to be loaded.

#### 10XXX — Function code is specified as bits XXX.

#### 01DDD — Function code is specified as bits 2–0 of data register DDD.

#### 00000 — Function code is specified as SFC register.

#### 00001 — Function code is specified as DFC register.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-47

# PMOVE Move to/from MMU Registers PMOVE

#### (MC68030 only)

#### Operation: If Supervisor State

#### Then (Source) → MRn or MRn → (Destination)

#### Assembler PMOVE MRn, < ea >

#### Syntax: PMOVE < ea > ,MRn

#### PMOVEFD < ea > ,MRn

#### Attributes: Size = (Word, Long, Quad)

#### Description: Moves the contents of the source effective address to the specified memory

#### management unit register or moves the contents of the memory management unit

#### register to the destination effective address.

#### The instruction is a quad-word (8 byte) operation for the CPU root pointer and the

#### supervisor root pointer. It is a long-word operation for the translation control register

#### and the transparent translation registers (TT0 and TT1). It is a word operation for the

#### MMU status register.

#### The PMOVEFD form of this instruction sets the FD-bit to disable flushing the address

#### translation cache when a new value loads into the supervisor root pointer, CPU root

#### pointer, TT0, TT1 or translation control register (but not the MMU status register).

#### Writing to the following registers has the indicated side effects:

#### CPU Root Pointer—When the FD-bit is zero, it flushes the address translation cache.

#### If the operand value is invalid for a root pointer descriptor, the instruction takes an

#### memory management unit configuration error exception after moving the operand to

#### the CPU root pointer.

#### Supervisor Root Pointer—When the FD-bit is zero, it flushes the address translation

#### cache. If the operand value is invalid as a root pointer descriptor, the instruction takes

#### an memory management unit configuration error exception after moving the operand

#### to the supervisor root pointer.

#### Translation Control Register—When the FD-bit is zero, it flushes the address transla-

#### tion cache. If the E-bit = 1, consistency checks are performed on the PS and TIx fields.

#### If the checks fail, the instruction takes an memory management unit configuration

#### exception after moving the operand to the translation control register. If the checks

#### pass, the translation control register is loaded with the operand and the E-bit is cleared.

#### TT0, TT1—When the FD-bit is zero, it flushes the address translation cache. It enables

#### or disables the transparent translation register according to the E-bit written. If the E-

#### bit = 1, the transparent translation register is enabled. If the E- bit = 0, the register is

#### disabled.


##### Supervisor (Privileged) Instructions

##### 6-48 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PMOVE Move to/from MMU Registers PMOVE

#### (MC68030 only)

#### Condition Codes:

#### Not affected.

#### MMU Status Register:

#### Not affected (unless the MMU status register is specified as the destination operand).

#### Instruction Format:

##### SRP, CRP, and TC Registers

#### Instruction Fields:

#### Effective Address field—Specifies the memory location for the transfer. Only control

#### alterable addressing modes can be used as in the following table:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 1 0 P-REGISTER R/ W FD 0 0 0 0 0 0 0 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-49

# PMOVE Move to/from MMU Registers PMOVE

#### (MC68030 only)

#### P-Register field—Specifies the memory management unit register.

#### 000—Translation Control Register

#### 010—Supervisor Root Pointer

#### 011—CPU Root Pointer

#### R/W field—Specifies the direction of transfer.

#### 0—Memory to memeory management unit register.

#### 1—Memeory management unit register to memory.

#### FD field—Disables flushing of the address translation cache on writes to memeory

#### management unit registers.

#### 0—Address translation cache is flushed.

#### 1—Address translation cache is not flushed.

#### Instruction Format:

##### MMU Status Register

#### Instruction Fields:

#### Effective Address field—Specifies the memory location for the transfer. Control

#### alterable addressing modes shown for supervisor root pointer register apply.

#### R/W field—Specifies the direction of transfer.

#### 0—Memory to MMU status register.

#### 1—MMU status register to memory.

#### NOTE

#### The syntax of assemblers for the MC68851 use the symbol

#### PMMU status register for the MMU status register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 1 1 0 0 0 R/ W 0 0 0 0 0 0 0 0 0


##### Supervisor (Privileged) Instructions

##### 6-50 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PMOVE Move to/from MMU Registers PMOVE

#### (MC68030 only)

#### Instruction Format:

##### TT Registers

#### Instruction Fields:

#### Effective Address field—Specifies the memory location for the transfer. Control

#### alterable addressing modes shown for supervisor root pointer register apply.

#### P-Register field—Specifies the transparent translation register.

#### 010—Transparent Translation Register 0

#### 011—Transparent Translation Register 1

#### R/W field—Specifies the direction of transfer.

#### 0—Memory to MMU status register.

#### 1—MMU status register to memory.

#### FD field—Disables flushing of the address translation cache.

#### 0—Address translation cache is flushed.

#### 1—Address translation cache does not flush.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 P-REGISTER R/ W FD 0 0 0 0 0 0 0 0


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-51

# PMOVE Move to/from MMU Registers PMOVE

#### (MC68EC030)

#### Operation: If Supervisor State

#### Then (Source) → MRn or MRn → (Destination)

#### Assembler PMOVE MRn, < ea >

#### Syntax: PMOVE < ea > ,MRn

#### Attributes: Size = (Word, Long, Quad)

#### Description: Moves the contents of the source effective address to an access control

#### register or moves the contents of an access control register to the destination effective

#### address.

#### The instruction is a long-word operation for the access control registers (AC0 and

#### AC1). It is a word operation for the access control unit status register (ACUSR).

#### Writing to the ACx registers enables or disables the access control register according

#### to the E-bit written. If the E-bit = 1, the access control register is enabled. If the E-bit =

#### 0, the register is disabled

#### Condition Codes:

#### Not affected.

#### ACUSR:

#### Not affected unless the ACUSR is specified as the destination operand.

#### Instruction Format:

##### ACUSR

#### Instruction Fields:

#### Effective Address field—Specifies the memory location for the transfer.

#### R/W field—Specifies the direction of transfer.

#### 0—Memory to ACUSR

#### 1—ACUSR to memory

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 1 1 0 0 0 R/W 0 0 0 0 0 0 0 0 0


##### Supervisor (Privileged) Instructions

##### 6-52 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PMOVE Move to/from MMU Registers PMOVE

#### (MC68EC030)

#### NOTE

#### Assembler syntax for the MC68851 uses the symbol PMMU

#### status register for the ACUSR; and for the MC68030, the

#### symbols TT0 and TT1 for AC0 and AC1.

#### Instruction Format:

##### ACx Registers

#### Instruction Fields:

#### Effective Address field—Specifies the memory location for the transfer.

#### P-Register field—Specifies the ACx register.

#### 001—Access Control Register 0

#### 011—Access Control Register 1

#### R/W field—Specifies the direction of transfer.

#### 0—Memory to ACUSR

#### 1—ACUSR to memory

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 0 0 P-REGISTER R/W 0 0 0 0 0 0 0 0 0


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-53

# PMOVE Move PMMU Register PMOVE

#### (MC68851)

#### Operation: If Supervisor State

#### Then MC68851 Register →Destination

#### Or Source → MC68851 Register

#### Else TRAP

#### Assembler PMOVE < PMMU Register > , < ea >

#### Syntax: PMOVE < ea > , < PMMU Register >

#### Attributes: Size = (Byte, Word, Long, Double Long)

#### Description: The contents of the MC68851 register copies to the address specified by < ea

#### > , or the data at < ea > copies into the MC68851 register.

#### The instruction is a quad-word operation for CPU root pointer, supervisor root pointer,

#### and DMA root pointer registers. It is a long-word operation for the translation control

#### register and a word operation for the breakpoint acknowledge control, breakpoint

#### acknowledge data, access control, PMMU status, and PMMU cache status registers.

#### PMOVE is a byte operation for the current access level, valid access level, and stack

#### change control registers.

#### The following side effects occur when data is read into certain registers:

#### CPU Root Pointer—Causes the internal root pointer table to be searched for the

#### new value. If there is no matching value, an entry in the root pointer table is selected

#### for replacement, and all address translation cache entries associated with the

#### replaced entry are invalidated.

#### Supervisor Root Pointer—Causes all entries in the address translation cache that

#### were formed with the supervisor root pointer (even globally shared entries) to be

#### invalidated.

#### DMA Root Pointer—Causes all entries in the address translation cache that were

#### formed with the DMA root pointer (even globally shared entries) to be invalidated.

#### Translation Control Register—If data written to the translation control register

#### attempts to set the E-bit and the E-bit is currently clear, a consistency check is per-

#### formed on the IS, TIA, TIB, TIC, TID, and PS fields.


##### Supervisor (Privileged) Instructions

##### 6-54 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PMOVE Move PMMU Register PMOVE

#### (MC68851)

#### PMMU Status Register: Not affected unless the PMMU status register is written to by the

#### instruction.

#### Instruction Format 1:

#### PMOVE to/from TC, CRP, DRP, SRP, CAL, VAL, SCC, AC

#### Instruction Fields:

#### Effective Address field—for memory-to-register transfers, any addressing mode is

#### allowed as listed in the following table:

```
*PMOVE to CRP, SRP, and DMA root pointer not allowed with these modes
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESSREGISTER
0 1 0 P-REGISTER R/ W 0 0 0 0 0 0 0 0 0
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn* 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An # < data > 111 100
(An) + 011 reg. number:An
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) 111 011
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) 111 011


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-55

# PMOVE Move PMMU Register PMOVE

#### (MC68851)

#### For register-to-memory transfers, only alterable addressing modes can be used as

#### listed in the following table:

```
*PMOVE to CRP, SRP, and DMA root pointer not allowed with these modes
```
#### Register field—Specifies the MC68851 register.

#### 000—Translation Control Register

#### 001—DMA Root Pointer

#### 010—Supervisor Root Pointer

#### 011—CPU Root Pointer

#### 100—Current Access Level

#### 101—Valid Access Level

#### 110—Stack Change Control Register

#### 111—Access Control Register

#### R/W field—Specifies the direction of transfer.

#### 0—Transfer < ea > to MC68851 register.

#### 1—Transfer MC68851 register to < ea >.

#### Instruction Format 2:

##### PMOVE to/from BADx, BACx

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn* 000 reg. number:Dn (xxx).W 111 000
An* 001 reg. number:An (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 1 1 P-REGISTER R/ W 0 0 0 0 NUM 0 0


##### Supervisor (Privileged) Instructions

##### 6-56 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PMOVE Move PMMU Register PMOVE

#### (MC68851)

#### Instruction Fields:

#### Effective Address field—Same as format 1.

#### P-Register field—Specifies the type of MC68851 register.

#### 100—Breakpoint Acknowledge Data

#### 101—Breakpoint Acknowledge Control

#### R/W field—Specifies the direction of transfer.

#### 0—Transfer < ea > to MC68851 register

#### 1—Transfer MC68851 register to < ea >

#### Num field—Specifies the number of the BACx or BADx register to be used.

#### Instruction Format 3:

##### PMOVE to/from PSR, from PCSR

#### Instruction Fields:

#### Effective Address field—Same as format 1.

#### P Register field—Specifies the MC68851 register.

#### 000 — PMMU Status Register

#### 001 — PMMU Cache Status Register

#### R/W field—Specifies direction of transfer.

#### 0—Transfer < ea > to MC68851 register.

#### 1—Transfer MC68851 register to < ea > (must be one to access PMMU cache

#### status register using this format).

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111 0 00000) MODEEFFECTIVE ADDRESS REGISTER
0 1 1 P-REGISTER R/ W 0 0 0 0 0 0 0 0 0


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-57

# PRESTORE PMMU Restore Function PRESTORE

#### (MC68851)

#### Operation: If Supervisor State

#### Then MC68851 State Frame → Internal State, Programmer

#### Registers

#### Else TRAP

#### Assembler

#### Syntax: PRESTORE < ea >

#### Attributes: Unsized, Privileged

#### Description: The MC68851 aborts execution of any operation in progress. New

#### programmer registers and internal states are loaded from the state frame located at the

#### effective address. The first word at the specified address is the format word of the state

#### frame, specifying the size of the frame and the revision number of the MC68851 that

#### created it. The MC68020 writes the first word to the MC68851 restore coprocessor

#### interface register, initiating the restore operation. Then it reads the response

#### coprocessor interface register to verify that the MC68851 recognizes the format as

#### valid. The format is invalid if the MC68851 does not recognize the frame size or the

#### revision number does not match. If the format is invalid, the MC68020 takes a format

#### exception, and the MC68851 returns to the idle state with its user visible registers

#### unchanged. However, if the format is valid, then the appropriate state frame loads,

#### starting at the specified location and proceeding up through the higher addresses.

#### The PRESTORE instruction restores the nonuser visible state of the MC68851 as well

#### as the PMMU status register, CPU root pointer, supervisor root pointer, current access

#### level, valid access level, and stack change control registers of the user programming

#### model. In addition, if any breakpoints are enabled, all breakpoint acknowledge control

#### and breakpoint acknowledge data registers are restored. This instruction is the inverse

#### of the PSAVE instruction.

#### The current implementation of the MC68851 supports four state frame sizes:

#### NULL: This state frame is 4 bytes long, with a format word of $0. A PRESTORE with

#### this size state frame places the MC68851 in the idle state with no coproces-

#### sor or module operations in progress.

#### IDLE: This state frame is 36 ($24) bytes long. A PRESTORE with this size state

#### frame causes the MC68851 to place itself in an idle state with no coproces-

#### sor operations in progress and no breakpoints enabled. A module operation

#### may or may not be in progress. This state frame restores the minimal set of

#### MC68851 registers.


##### Supervisor (Privileged) Instructions

##### 6-58 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PRESTORE PMMU Restore Function PRESTORE

#### (MC68851)

#### MID-COPROCESSOR: This state frame is 44 ($2C) bytes long. A PRESTORE with

#### this size frame restores the MC68851 to a state with a coprocessor operation

#### in progress and no breakpoints enabled.

#### BREAKPOINTS ENABLED: This state frame is 76 ($4C) bytes long. A PRESTORE

#### with this size state frame restores all breakpoint registers, along with other

#### states. A coprocessor operation may or may not be in progress.

#### PMMU Status Register: Set according to restored data.

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies the source location. Only control or post-increment

#### addressing modes can be used as listed in the following table:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000101) MODEEFFECTIVE ADDRESS REGISTER
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) 111 011
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) 111 011


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-59

# PSAVE PMMU Save Function PSAVE

#### (MC68851)

#### Operation: If Supervisor State

#### Then MC68851 Internal State, Programmer

#### Registers → State Frame

#### Else TRAP

#### Assembler

#### Syntax: PSAVE < ea >

#### Attributes: Unsized, Privileged

#### Description: The MC68851 suspends execution of any operation that it is performing and

#### saves its internal state and some programmer registers in a state frame located at the

#### effective address. The following registers are copied: PMMU status, control root

#### pointer, supervisor root pointer, current access level, valid access level, and stack

#### change control. If any breakpoint is enabled, all breakpoint acknowledge control and

#### breakpoint acknowledge data registers are copied. After the save operation, the

#### MC68851 is in an idle state waiting for another operation to be requested. Programmer

#### registers are not changed.

#### The state frame format saved by the MC68851 depends on its state at the time of the

#### PSAVE operation. In the current implementation, three state frames are possible:

#### IDLE: This state frame is 36 ($24) bytes long. A PSAVE of this size state frame indi-

#### cates that the MC68851 was in an idle state with no coprocessor operations

#### in progress and no breakpoints enabled. A module call operation may or may

#### not have been in progress when this state frame was saved.

#### MID-COPROCESSOR:This state frame is 44 ($2C) bytes long. A PSAVE of this size

#### frame indicates that the MC68851 was in a state with a coprocessor or mod-

#### ule call operation in progress and no breakpoints enabled.

#### BREAKPOINTS ENABLED:This state frame is 76 ($4C) bytes long. A PSAVE of this

#### size state frame indicates that one or more breakpoints were enabled. A

#### coprocessor or module call operation may or may not have been in progress.

#### PMMU Status Register: Not affected


##### Supervisor (Privileged) Instructions

##### 6-60 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PSAVE PMMU Save Function PSAVE

#### (MC68851)

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only control or

#### predecrement addressing modes can be used as listed in the following table:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000100) MODEEFFECTIVE ADDRESS REGISTER
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-61

# PScc Set on PMMU unit Condition PScc

#### (MC68851)

#### Operation: If Supervisor State

#### Then If cc True

#### Then 1s → Destination

#### Else 0s → Destination

#### Else TRAP

#### Assembler

#### Syntax: PScc < ea >

#### Attributes: Size = (Byte)

#### Description: The specified MC68851 condition code is tested. If the condition is true, the

#### byte specified by the effective address is set to TRUE (all ones); otherwise, that byte is

#### set to FALSE (all zeros).

#### The condition code specifier cc may specify the following conditions:

#### PMMU Status Register: Not affected

```
Specifier Description Condition Field Specifier Description Condition Field
BS B set 000000 BC B clear 000001
LS L set 000010 LC L clear 000011
SS S set 000100 SC S clear 000101
AS A set 000110 AC A clear 000111
WS W set 001000 WC W clear 001001
IS I set 001010 IC I clear 001011
GS G set 001100 GC G clear 001101
CS C set 001110 CC C clear 001111
```

##### Supervisor (Privileged) Instructions

##### 6-62 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PScc Set on PMMU Condition PScc

#### (MC68851)

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies the destination location. Only data alterable

#### addressing modes can be used as listed in the following table:

#### MC68851 Condition field—Specifies the coprocessor condition to be tested. This field

#### is passed to the MC68851, which provides directives to the main processor for

#### processing this instruction.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000001) MODEEFFECTIVE ADDRESS REGISTER
0000000000 MC68851 CONDITION
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn 000 reg. number:Dn (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + 011 reg. number:An
—(An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-63

# PTEST Test a Logical Address PTEST

#### (MC68030 only)

#### Operation: If Supervisor State

#### Then Logical Address Status → MMUSR

#### Else TRAP

#### Assembler PTESTR FC, < ea > ,# < level >

#### Syntax: PTESTR FC, < ea > ,# < level > ,An

#### PTESTW FC, < ea > ,# < level >

#### PTESTW FC, < ea > ,# < level > ,An

#### Attributes: Unsized

#### Description: This instruction searches the address translation cache or the translation

#### tables to a specified level. Searching for the translation descriptor corresponding to the

#### < ea > field, it sets the bits of the MMU status register according to the status of the

#### descriptor. Optionally, PTEST stores the physical address of the last table entry

#### accessed during the search in the specified address register. The PTEST instruction

#### searches the address translation cache or the translation tables to obtain status

#### information, but alters neither the used or modified bits of the translation tables nor the

#### address translation cache. When the level operand is zero, only the transparent

#### translation of either read or write accesses causes the operations of the PTESTR and

#### PTESTW to return different results.

#### The < function code > operand is specified as one of the following:

#### 1. Immediate—Three bits in the command word.

#### 2. Data Register—The three least significant bits of the data register specified in

#### the instruction.

#### 3. Source Function Code (SFC) Register

#### 4. Destination Function Code (DFC) Register

#### The effective address is the address to test. The < level > operand specifies the level

#### of the search. Level 0 specifies searching the addrass translation cache only. Levels

#### 1–7 specify searching the translation tables only. The search ends at the specified

#### level. A level 0 test does not return the same MMU status register values as a test at a

#### nonzero level number.

#### Execution of the instruction continues to the requested level or until detecting one of

#### the following conditions:

- Invalid Descriptor
- Limit Violation
- Bus Error Assertion (Physical Bus Error)


##### Supervisor (Privileged) Instructions

##### 6-64 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTEST Test a Logical Address PTEST

#### (MC68030 only)

#### The instruction accumulates status as it accesses successive table entries. When the

#### instruction specifies an address translation cache search with an address register

#### operand, the MC68030 takes an F-line unimplemented instruction exception.

#### If there is a parameter specification for a translation table search, the physical address

#### of the last descriptor successfully fetched loads into the address register. A success-

#### fully fetched descriptor occurs only if all portions of the descriptor can be read by the

#### MC68030 without abnormal termination of the bus cycle. If the root pointer’s DT field

#### indicates page descriptor, the returned address is $0. For a long descriptor, the

#### address of the first long word is returned. The size of the descriptor (short or long) is

#### not returned and must be determined from a knowledge of the translation table.

#### Condition Codes:

#### Not affected.

#### MMUSR:

```
B L S W I M T N
∗ ∗∗ 0 ∗∗∗ 000000 ∗
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-65

# PTEST Test a Logical Address PTEST

#### (MC68030 only)

#### The MMU status register contains the results of the search. The values in the fields of

#### the MMU status register for an address translation cache search are given in the fol-

#### lowing table:

```
MMUSR Bit PTEST, Level 0 PTEST, Levels 1–7
Bus Error (B) This bit is set if the bus error bit is set in the
ATC entry for the specified logical address.
```
```
This bit is set if a bus error is encountered
during the table search for the PTEST in-
struction.
Limit (L) This bit is cleared. This bit is set if an index exceeds a limit
during the table search.
Supervis or
Violatio n (S)
```
```
This bit is cleared. This bit is set if the S-bit of a long (S) format
table descriptor or long format page de-
scriptor encountered during the search is
set and if the FC2-bit of the function code
specified by the PTEST instruction is not
equal to one. The S-bit is undefined if the I-
bit is set.
Write
Protecte d (W)
```
```
The bit is set if the WP-bit of the ATC entry
is set. It is undefined if the I-bit is set.
```
```
This bit is set if a descriptor or page de-
scriptor is encountered with the WP-bit set
during the table search. The W-bit is unde-
fined if the I-bit is set.
Invalid (I) This bit indicates an invalid translation. The
I- bit is set if the translation for the specified
logical address is not resident in the ATC
or if the B-bit of the corresponding ATC en-
try is set.
```
```
This bit indicates an invalid translation. The
I-bit is set if the DT field of a table or a page
descriptor encountered during the search
is set to invalid or if either the B or L bits of
the MMUSR are set during the table
search.
Modified (M) This bit is set if the ATC entry correspond-
ing to the specified address has the modi-
fied bit set. It is undefined if the I-bit is set.
```
```
This bit is set if the page descriptor for the
specified address has the modified bit set.
It is undefined if I-bit is set.
Transparent (T) This bit is set if a match occurred in either
(or both) of the transparent translation reg-
isters (TT0 or TT1).
```
```
This bit is set to zero.
```
```
Number of
Levels (N)
```
```
This 3-bit field is set to zero. This 3-bit field contains the actual number
of tables accessed during the search.
```

##### Supervisor (Privileged) Instructions

##### 6-66 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTEST Test a Logical Address PTEST

#### (MC68030 only)

#### Instruction Format:

#### Instruction Fields:

#### Effective Address field—Specifies the logical address to be tested. Only control

#### alterable addressing modes can be used as listed in the following table:

#### Level field—Specifies the highest numbered level to be searched in the table. When

#### this field contains 0, the A field and the register field must also be 0. The

#### instruction takes an F-line exception when the level field is 0 and the A field is not

#### 0.

#### R/W field—Specifies simulating a read or write bus cycle (no difference for MC68030

#### MMU).

#### 0—Write

#### 1—Read

#### A field—Specifies the address register option.

#### 0—No address register.

#### 1—Return the address of the last descriptor searched in the address register spec-

#### ified in the register field.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
1 0 0 LEVEL R/ W A REGISTER FC
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-67

# PTEST Test a Logical Address PTEST

#### (MC68030 only)

#### Register field—Specifies an address register for the instruction. When the A field

#### contains 0, this field must contain 0.

#### FC field—Function code of address to be tested.

#### 10XXX — Function code is specified as bits XXX.

#### 01DDD — Function code is specified as bits 2–0 of data register DDD.

#### 00000 — Function code is specified as source function code register.

#### 00001 — Function code is specified as destination function code register.


##### Supervisor (Privileged) Instructions

##### 6-68 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTEST Test a Logical Address PTEST

#### (MC68EC030)

#### Operation: If Supervisor State

#### Then Logical Address Status → ACUSR

#### Else TRAP

#### Assembler PTESTR FC, < ea >

#### Syntax: PTESTW FC, < ea >

#### Attributes: Unsized

#### Description: This instruction searches the access control registers for the address

#### descriptor corresponding to the < ea > field and sets the bit of the access control unit

#### status register (ACUSR) according to the status of the descriptor.

#### The < function code > operand is specified in one of the following ways:

#### 1. Immediate—Three bits in the command word.

#### 2. Data Register—The three least significant bits of the data register specified in

#### the instruction.

#### 3. Source Function Code (SFC) Register

#### 4. Destination Function Code (DFC) Register

#### The effective address is the address to test.

#### Condition Codes:

#### Not affected.

#### ACUSR:

x = May be 0 or 1.

#### The AC-bit is set if a match occurs in either (or both) of the access control registers.

#### Instruction Format:

```
x x x 0 x x x 0 0 AC 0 0 0 x x x
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
1 0 0 0 0 0 R/ W 0 REGISTER FC


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-69

# PTEST Test a Logical Address PTEST

#### (MC68EC030)

#### Instruction Fields:

#### Effective Address field—Specifies the logical address to be tested. Only control

#### alterable addressing modes can be used as listed in the following table:

#### R/W field—Specifies simulating a read or write bus cycle.

#### 0—Write

#### 1—Read

#### Register field—Specifies an address register for the instruction. When the A field

#### contains 0, this field must contain 0.

#### FC field—Function code of address to be tested.

#### 10XXX — Function code is specified as bits XXX.

#### 01DDD — Function code is specified as bits 2–0 of data register DDD.

#### 00000 — Function code is specified as source function code register.

#### 00001 — Function code is specified as destination function code register.

#### NOTE

#### Assembler syntax for the MC68030 is PTESTR FC, < ea > ,#0

#### and PTESTW FC, < ea > ,#0.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —
```

##### Supervisor (Privileged) Instructions

##### 6-70 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTEST Test a Logical Address PTEST

#### (MC68040, MC68LC040)

#### Operation: If Supervisor State

#### Then Logical Address Status → MMUSR; Entry → ATC

#### Else TRAP

#### Assembler PTESTR (An)

#### Syntax: PTESTW (An)

#### Attributes: Unsized

#### Description: This instruction searches the translation tables for the page descriptor

#### corresponding to the test address in An and sets the bits of the MMU status register

#### according to the status of the descriptors. The upper address bits of the translated

#### physical address are also stored in the MMU status register. The PTESTR instruction

#### simulates a read access and sets the U-bit in each descriptor during table searches;

#### PTESTW simulates a write access and also sets the M-bit in the descriptors, the

#### address translation cache entry, and the MMU status register.

#### A matching entry in the address translation cache (data or instruction) specified by the

#### function code will be flushed by PTEST. Completion of PTEST results in the creation

#### of a new address translation cache entry. The specification of the function code for the

#### test address is in the destination function code (DFC) register. A PTEST instruction

#### with a DFC value of 0, 3, 4, or 7 is undefined and will return an unknown value in the

#### MMUSR.

#### Execution of the instruction continues until one of the following conditions occurs:

- Match with one of the two transparent translation registers.
- Transfer Error Assertion (physical transfer error)
- Invalid Descriptor
- Valid Page Descriptor

#### Condition Codes:

#### Not affected.

#### MMU Status Register:

```
PHYSICAL ADDRESS B G U1 U0 S CM M W T R
∗∗∗∗∗ ∗∗ ∗ 0 ∗∗ ∗
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-71

# PTEST Test a Logical Address PTEST

#### (MC68040, MC68LC040)

#### The MMUSR contains the results of the search. The values in the fields of the MMUSR

#### for a search are:

#### Physical Address—This 20-bit field contains the upper bits of the translated physical

#### address. Merging these bits with the lower bits of the logical address forms the

#### actual physical address.

#### Bus Error (B)—Set if a transfer error is encountered during the table search for the

#### PTEST instruction. If this bit is set, all other bits are zero.

#### Globally Shared (G)—Set if the G-bit is set in the page descriptor.

#### User Page Attributes (U1, U0)—Set if corresponding bits in the page descriptor are set.

#### Supervisor Protection (S)—Set if the S-bit in the page descriptor is set. This bit does

#### not indicate that a violation has occurred.

#### Cache Mode (CM)—This 2-bit field is copied from the CM-bit in the page descriptor.

#### Modified (M)—Set if the M-bit is set in the page descriptor associated with the address.

#### Write Protect (W)—Set if the W-bit is set in any of the descriptors encountered during

#### the table search. Setting of this bit does not indicate that a violation occurred.

#### Transparent Translation Register Hit (T)—Set if the PTEST address matches an

#### instruction or data transparent translation register and the R-bit is set; all other bits

#### are zero.

#### Resident (R)—Set if the PTEST address matches a transparent translation register or

#### if the table search completes by obtaining a valid page descriptor.

#### Instruction Format:

#### Instruction Fields:

#### R/W field—Specifies simulating a read or write bus transfer.

#### 0—Write

#### 1—Read

#### Register field—Specifies the address register containing the effective address for the

#### instruction.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1 1 1 1 0 1 0 1 0 1 R/ W 0 1 REGISTER
```

##### Supervisor (Privileged) Instructions

##### 6-72 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTEST Test a Logical Address PTEST

#### (MC68EC040)

#### Operation: If Supervisor State

#### Then No Operation, Possibly Run Extraneous Bus Cycles

#### Else TRAP

#### Assembler PTESTR (An)

#### Syntax: PTESTW (An)

#### Attributes: Unsized

#### Description: This instruction must not be executed on an MC68EC040. This instruction

#### may cause extraneous bus cycles to occur and may result in unexpected exception

#### types.

#### Instruction Format:

#### Instruction Fields:

#### R/W field—Specifies simulating a read or write bus transfer.

#### 0—Write

#### 1—Read

#### Register field—Specifies the address register containing the effective address for the

#### instruction.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1 1 1 1 0 1 0 1 0 1 R/ W 0 1 REGISTER
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-73

# PTEST Get Information About Logical Address PTEST

#### (MC68851)

#### Operation: If Supervisor State

#### Then Information About Logical Address → PSTATUS

#### Else TRAP

#### Assembler PTESTR FC, < ea > ,# < level > ,(An)

#### Syntax: PTESTW FC, < ea > ,# < level > ,(An)

#### Attributes: Unsized

#### Description: If the E-bit of the translation control register is set, information about the logical

#### address specified by FC and < ea > is placed in the PMMU status register. If the E-bit

#### of the translation control register is clear, this instruction will cause a paged memory

#### management unit illegal operation exception (vector $39).

#### The function code for this operation may be specified as follows:

#### 1. Immediate—The function code is four bits in the command word.

#### 2. Data Register—The function code is in the lower four bits in the MC68020 data

#### register specified in the instruction.

#### 3. Source Function Code (SFC) Register—The function code is in the SFC register

#### in the CPU. Since the SFC of the MC68020 has only three implemented bits,

#### only function codes $0D$7 can be specified in this manner.

#### 4. Destination Function Code (DFC) Register—The function code is in the DFC

#### register in the CPU. Since the DFC of the MC68020 has only three implemented

#### bits, only function codes $0D$7 can be specified in this manner.

#### The effective address field specifies the logical address to be tested.

#### The # < level > parameter specifies the depth to which the translation table is to be

#### searched. A value of zero specifies a search of the address translation cache only. Val-

#### ues 1–7 cause the address translation cache to be ignored and specify the maximum

#### number of descriptors to fetch.

#### NOTE

#### Finding an address translation cache entry with < level > set to

#### zero may result in a different value in the PMMU status register

#### than forcing a table search. Only the I, W, G, M, and C bits of the

#### PMMU status register are always the same in both cases.


##### Supervisor (Privileged) Instructions

##### 6-74 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTEST Get Information About Logical Address PTEST

#### (MC68851)

#### Either PTESTR or PTESTW must be specified. These two instructions differ in the set-

#### ting of the A-bit of the PMMU status register. For systems where access levels are not

#### in use, either PTESTR or PTESTW may be used. U and M bits in the translation table

#### are not modified by this instruction.

#### If there is a specified address register parameter, the physical address of the last suc-

#### cessfully fetched descriptor is loaded into the address register. A descriptor is success-

#### fully fetched if all portions of the descriptor can be read by the MC68851 without

#### abnormal termination of the bus cycle. If the DT field of the root pointer used indicates

#### page descriptor, the returned address is $0.

#### The PTEST instruction continues searching the translation tables until reaching the

#### requested level or until a condition occurs that makes further searching impossible (i.e.,

#### a DT field set to invalid, a limit violation, or a bus error from memory). The information

#### in the PMMU status register reflects the accumulated values.

#### PMMU Status Register:

#### Bus Error (B)—Set if a bus error was received during a descriptor fetch, or if < level >

#### = 0 and an entry was found in the address translation cache with its BERR bit set;

#### cleared otherwise.

#### Limit (L)—Set if the limit field of a long descriptor was exceeded; cleared otherwise.

#### Supervisor Violation (S)—Set if a long descriptor indicated supervisor-only access and

#### the < fc > parameter did not have bit 2 set; cleared otherwise.

#### Access Level Violation (A)—If PTESTR was specified, set if the RAL field of a long

#### descriptor would deny access. If PTESTW was specified, set if a WAL or RAL field

#### of a long descriptor would deny access; cleared otherwise.

#### Write Protection (W)—Set if the WP-bit of a descriptor was set or if a WAL field of a

#### long descriptor would deny access; cleared otherwise.

#### Invalid (I)—Set if a valid translation was not available; cleared otherwise.

#### Modified (M)—If the tested address is found in the address translation cache, set to the

#### value of the M-bit in the address translation cache. If the tested address is found

#### in the translation table, set if the M-bit of the page descriptor is set; cleared

#### otherwise.


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-75

# PTEST Get Information About Logical Address PTEST

#### (MC68851)

#### Gate (G)—If the tested address is found in the address translation cache, set to the

#### value of the G-bit in the address translation cache. If the tested address is found in

#### the translation table, set if the G-bit of the page descriptor is set; cleared otherwise.

#### Globally Shared (C)—Set if the address is globally shared; cleared otherwise.

#### Level Number (N)—Set to the number of levels searched. A value of zero indicates an

#### early termination of the table search in the root pointer (DT = page descriptor) if

#### the level specification was not zero. If the level specification was zero, N is always

#### set to zero.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
1 0 0 LEVEL R/ W A-REGISTER FC


##### Supervisor (Privileged) Instructions

##### 6-76 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTEST Get Information About Logical Address PTEST

#### (MC68851)

#### Instruction Fields:

#### Effective Address field—Specifies the logical address about which information is

#### requested. Only control alterable addressing modes can be used as listed in the

#### following table:

#### NOTE

#### The effective address field must provide the MC68851 with the

#### effective address of the logical address to be tested, not the

#### effective address describing where the PTEST operand is

#### located. For example, to test a logical address that is temporarily

#### stored on the system stack, the instruction PTEST [(SP)] must

#### be used since PTEST (SP) would test the mapping of the system

#### stack (i.e., the effective address passed to the MC68851 is the

#### effective address of the system stack, not the effective address

#### formed by the operand located on the top of the stack).

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-77

# PTEST Get Information About Logical Address PTEST

#### (MC68851)

#### Level field—Specifies the depth to which the translation table should be searched.

#### R/W field—Specifies whether the A-bit should be updated for a read or a write.

#### 1—Read

#### 0—Write

#### A-Register field—Specifies the address register in which to load the last descriptor

#### address.

#### 0xxx — Do not return the last descriptor address to an address register.

#### 1RRR — Return the last descriptor address to address register RRR.

#### NOTE

#### When the PTEST instruction specifies a level of zero, the A-

#### register field must be 0000. Otherwise, an F-line exception is

#### generated.

#### FC field—Function code of address to test.

#### 1DDDD — Function code is specified as four bits DDDD.

#### 01RRR — Function code is contained in CPU data register RRR.

#### 00000 — Function code is contained in CPU source function code register.

#### 00001 — Function code is contained in CPU destination function code

#### register.


##### Supervisor (Privileged) Instructions

##### 6-78 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PTRAPcc TRAP on PMMU Condition PTRAPcc

#### (M68851)

#### Operation: If Supervisor State

#### Then If cc True

#### Then TRAP

#### Else TRAP

#### Assembler PTRAPcc

#### Syntax: PTRAPcc.W # < data > PTRAPcc.L # < data >

#### Attributes: Unsized or Size = (Word, Long)

#### Description: If the selected MC68851 condition is true, the processor initiates exception

#### processing. The vector number is generated referencing the cpTRAPcc exception

#### vector; the stacked program counter is the address of the next instruction. If the

#### selected condition is not true, no operation is performed, and execution continues with

#### the next instruction. The immediate data operand is placed in the next word(s) following

#### the MC68851 condition and is available for user definition to be used within the trap

#### handler. Following the condition word, there may be a user-defined data operand,

#### specified as immediate data, to be used by the trap handler.

#### The condition specifier cc may specify the following conditions:

#### PMMU Status Register: Not affected

```
Specifier Description Condition Field Specifier Description Condition Field
BS B set 000000 BC B clear 000001
LS L set 000010 LC L clear 000011
SS S set 000100 SC S clear 000101
AS A set 000110 AC A clear 000111
WS W set 001000 WC W clear 001001
IS I set 001010 IC I clear 001011
GS G set 001100 GC G clear 001101
CS C set 001110 CC C clear 001111
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-79

# PTRAPcc TRAP on PMMU Condition PTRAPcc

#### (M68851)

#### Instruction Format:

#### Instruction Fields:

#### Opmode field—Selects the instruction form.

#### 010 — Instruction is followed by one operand word.

#### 011 — Instruction is followed by two operand words.

#### 100 — Instruction has no following operand words.

#### MC68851 Condition field—Specifies the coprocessor condition to be tested. This field

#### is passed to the MC68851, which provides directives to the main processor for

#### processing this instruction.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111000001111 OPMODE
0000000000 MC68851 CONDITION
16-BIT OPERAND OR MOST SIGNIFICANT WORD OF 32-BIT OPERAND (IFNEEDED)
LEAST SIGNIFICANT WORD OF 32-BIT OPERAND (IF NEEDED)
```

##### Supervisor (Privileged) Instructions

##### 6-80 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PVALID Validate a Pointer PVALID

#### (MC68851)

#### Operation: If (Source AL Bits) → (Destination AL Bits)

#### Then TRAP

#### Assembler PVALID VAL, < ea >

#### Syntax: PVALID An, < ea >

#### Attributes: Size = (Long)

#### Description: The upper bits of the source, VAL or An, compare with the upper bits of the

#### destination, < ea >. The ALC field of the access control register defines the number of

#### bits compared. If the upper bits of the source are numerically greater than (less

#### privileged than) the destination, they cause a memory management access level

#### exception. Otherwise, execution continues with the next instruction. If the MC field of

#### the access control register = 0, then this instruction always causes a paged memory

#### management unit access level exception.

#### PMMU Status Register: Not affected.

#### Instruction Format 1:

##### VAL Contains Access Level to Test Against

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0 0 1 0 1 0 0 0 0 0 0 0 0 0 0 0


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-81

# PVALID Validate a Pointer PVALID

#### (MC68851)

#### Instruction Field:

#### Effective Address field—Specifies the logical address to be evaluated and compared

#### against the valid access level register. Only control alterable addressing modes can

#### be used as listed in the following table:

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —
```

##### Supervisor (Privileged) Instructions

##### 6-82 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# PVALID Validate a Pointer PVALID

#### (MC68851)

#### Instruction Format 2:

##### Main Processor Register Contains Access Level to Test Against

#### Instruction Fields:

#### Effective Address field—Specifies the logical address to be evaluated and compared

#### against specified main processor address register. Only control alterable addressing

#### modes can be used as listed in the following table:

#### NOTE

#### The effective address field must provide the MC68851 with the

#### effective address of the logical address to be validated, not the

#### effective address describing where the PVALID operand is

#### located. For example, to validate a logical address that is

#### temporarily stored on the system stack, the instruction PVALID

#### VAL,[(SP)] must be used since PVALID VAL,(SP) would validate

#### the mapping on the system stack (i.e., the effective address

#### passed to the MC68851 is the effective address of the system

#### stack, not the effective address formed by the operand located

#### on the top of the stack).

#### Register field—Specifies the main processor address register to be used in the

#### compare.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111000000) MODEEFFECTIVE ADDRESS REGISTER
0010100000000 REGISTER
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —
—(An) — —
(d 16 ,An) 101 reg. number:An (d 16 ,PC) — —
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) — —
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) — —
([bd,An,Xn] ,od) 110 reg. number:An ([bd,PC,Xn] ,od) — —
([bd,An],Xn ,od) 110 reg. number:An ([bd,PC],Xn ,od) — —


##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-83

# RESET Reset External Devices RESET

#### (M68000 Family)

#### Operation: If Supervisor State

#### Then Assert RESET (RSTO, MC68040 Only) Line

#### Else TRAP

#### Assembler

#### Syntax: RESET

#### Attributes: Unsized

#### Description: Asserts the RSTO signal for 512 (124 for MC68000, MC68EC000,

#### MC68HC000, MC68HC001, MC68008, MC68010, and MC68302) clock periods,

#### resetting all external devices. The processor state, other than the program counter, is

#### unaffected, and execution continues with the next instruction.

#### Condition Codes:

#### Not affected.

#### Instruction Format:

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 0 0 0
```

##### Supervisor (Privileged) Instructions

##### 6-84 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# RTE Return from Exception RTE

#### (M68000 Family)

#### Operation: If Supervisor State

#### Then (SP) → SR; SP + 2 → SP; (SP) → PC; SP + 4 → SP; Restore

#### State and Deallocate Stack According to (SP)

#### Else TRAP

#### Assembler

#### Syntax: RTE

#### Attributes: Unsized

#### Description: Loads the processor state information stored in the exception stack frame

#### located at the top of the stack into the processor. The instruction examines the stack

#### format field in the format/offset word to determine how much information must be

#### restored.

#### Condition Codes:

#### Set according to the condition code bits in the status register value restored from the

#### stack.

#### Instruction Format:

#### Format/Offset Word (in Stack Frame):

##### MC68010, MC68020, MC68030, MC68040, CPU32

#### Format Field of Format/Offset Word:

#### Contains the format code, which implies the stack frame size (including the format/

#### offset word). For further information, refer to Appendix B Exception Processing

#### Reference.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 0 1 1
```
```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
FORMAT 0 0 VECTOR OFFSET
```

##### Supervisor (Privileged) Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 6-85

# STOP Load Status Register and Stop STOP

#### (M68000 Family)

#### Operation: If Supervisor State

#### Then Immediate Data → SR; STOP

#### Else TRAP

#### Assembler

#### Syntax: STOP # < data >

#### Attributes: Unsized

#### Description: Moves the immediate operand into the status register (both user and

#### supervisor portions), advances the program counter to point to the next instruction, and

#### stops the fetching and executing of instructions. A trace, interrupt, or reset exception

#### causes the processor to resume instruction execution. A trace exception occurs if

#### instruction tracing is enabled (T0 = 1, T1 = 0) when the STOP instruction begins

#### execution. If an interrupt request is asserted with a priority higher than the priority level

#### set by the new status register value, an interrupt exception occurs; otherwise, the

#### interrupt request is ignored. External reset always initiates reset exception processing.

#### Condition Codes:

#### Set according to the immediate operand.

#### Instruction Format:

#### Instruction Fields:

#### Immediate field—Specifies the data to be loaded into the status register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 1 1 0 0 1 1 1 0 0 1 0
IMMEDIATE DATA
```

##### Supervisor (Privileged) Instructions

##### 6-86 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA


##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 7-1

## SECTION 7

## CPU32 INSTRUCTIONS

#### This section describes the instructions provided for the CPU32. The CPU32 can execute

#### object code from an MC68000 and MC68010 and many of the instructions of the MC68020.

#### There are three new instructions provided for the CPU32: enter background mode (BGND),

#### low-power stop (LPSTOP), and table lookup and interpolate (TBLS, TBLSN, TBLU, and

#### TBLUN). Table 7-1 lists the MC68020 instructions not supported by the CPU32.

#### Table 7-1. MC68020 Instructions Not Supported

```
Mnemonic
```
##### Description

```
BFCHG Test Bit Field and Change
BFCLR Test Bit Field and Clear
BFEXTS Signed Bit Field Extract
BFEXTU Unsigned Bit Field Extract
BFFFO Bit Field Find First One
BFINS Bit Field Insert
BFSET Test Bit Field and Set
BFTST Test Bit Field
CALLM CALL Module
CAS Compare and Swap Operands
CAS2 Compare and Swap Dual Operands
cpBcc Branch on Coprocessor Condition
cpDBcc Test Coprocessor Condition Decrement and Branch
cpGEN Coprocessor General Function
cpRESTORE Coprocessor Restore Function
cpSAVE Coprocessor Save Function
cpScc Set on Coprocessor Condition
cpTRAPcc Trap on Coprocessor Condition
RTM Return from Module
PACK Pack BCD
UNPK Unpack BCD
```

##### CPU32 Instructions

##### 7-2

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

#### Addressing in the CPU32 is register oriented. Most instructions allow the results of the

#### specified operation to be placed either in a register or directly in memory. This flexibility

#### eliminates the need for extra instructions to store register contents in memory. Table 7- 2 lists

#### the M68000 family addressing modes with cross-references to the MC68000, MC68010,

#### CPU32, and MC68020. When referring to instructions in the previous sections, refer to Table

#### 7-2 to identify the addressing modes available to the CPU32. Table 7-3 lists the instructions

#### for the CPU32.

NOTE: Xn,SIZE*SCALE—Denotes index register n (data or address), the index size (W for word, L for long
word and scale factor (1, 2, 4, or 8 for no-word, long-word, or 8 for quad- word scaling, respectively).
X—Supported

#### Table 7-2. M68000 Family Addressing Modes

```
Addressing Mode
```
##### Syntax

##### MC68000

##### MC68010 CPU32 MC68020

```
Register Indirect Rn X X X
Address Register Indirect (An) X X X
Address Register Indirect with Postincrement (An) + X X X
Address Register Indirect with Postdecrement – (An) X X X
Address Register Indirect with Displacement (d
16
,An) X X X
Address Register Indirect with Index
(8-Bit Displacement) (d
8
,An,Xn) X X X
Address Register Indirect with Index
(Base Displacement) (d
8
,An,Xn
∗
SCALE) X X
Memory Indirect with Postincrement ([bd,An],Xn, od) X
Memory Indirect with Preincrement ([bd,An],Xn, od) X
Absolute Short (xxx).W X X X
Absolute Long (xxx).L X X X
Program Counter Indirect with Displacement (d
16
```
###### ,PC) X X X

```
Program Counter Indirect with Index
(8-Bit Displacement) (d
8
,PC,Xn) X X X
Program Counter Indirect with Index
(Base Displacement) (d
8
,PC,Xn*SC ALE) X X
Immediate # < data > X X X
PC Memory Indirect with Postincrement ([bd,PC],Xn, od) X
PC Memory Indirect with Predecrement ([bd,PC],Xn, od) X
```

##### CPU32 Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 7-3

#### Table 7-3. CPU32 Instruction Set

```
Mnemonic Description Mnemonic Description
ABCD
ADD
ADDA
ADDI
ADDQ
ADDX
AND
ANDI
ANDI to CCR
ANDI to SR
ASL, ASR
```
```
Add Decimal with Extend
Add
Add Address
Add Immediate
Add Quick
Add with Extend
Logical AND
Logical AND Immediate
AND Immediate to Condition Code
Register
AND Immediate to Status Register
Arithmetic Shift Left and Right
```
###### MOVE

###### MOVEA

```
MOVE from
CCR
Move from SR
MOVE to SR
MOVE USP
MOVEC
MOVEM
MOVEP
MOVEQ
MOVES
MULS
MULU
```
```
Move
Move Address
Move Condition Code Register
Move from Status Register
Move to Status Register
Move User Stack Pointer
Move Control Register
Move Multiple Registers
Move Peripheral
Move Quick
Move Alternate Address Space
Signed Multiply
Bcc Unsigned Multiply
BCHG
BCLR
BGND
BKPT
BRA
BSET
BSR
BTST
```
```
Branch Conditionally
Test Bit and Change
Test Bit and Clear
Enter Background Mode
Breakpoint
Branch
Test Bit and Set
Branch to Subroutine
Test Bit
```
###### NBCD

###### NEG

###### NEGX

###### NOP

###### NOT

```
Negate Decimal with Extend
Negate
Negate with Extend
No Operation
Logical Complement
PEA Push Effective Address
```
```
RESET
ROL, ROR
ROXL, ROXR
RTD
RTE
RTR
RTS
```
```
Reset External Devices
Rotate Left and Right
Rotate with Extend Left and Right
Return and Deallocate
Return from Exception
Return and Restore Codes
Return from Subroutine
```
###### CHK

###### CHK2

###### CLR

###### CMP

###### CMPA

###### CMPI

###### CMPM

###### CMP2

```
Check Register Against Bound
Check Register Against Upper and
Lower Bound
Clear
Compare
Compare Address
Compare Immediate
Compare Memory to Memory
Compare Register Against Upper and
Lower Bounds SBCDScc
STOP
SUB
SUBA
SUBI
SUBQ
SUBX
SWAP
```
```
Subtract Decimal with Extend
Set Conditionally
Stop
Subtract
Subtract Address
Subtract Immediate
Subtract Quick
Subtract with Extend
Swap Register Words
```
```
DBcc
DIVS, DIVSL
DIVU, DIVUL
```
```
Test Condition, Decrement, and
Branch
Signed Divide
Unsigned Divide
```
###### EOR

###### EORI

```
EORI to CCR
EORI to SR
EXG
EXT, LSR
```
```
Logical Exclusive-OR
Logical Exclusive-OR Immediate
Exclusive-OR Immediate to
Condition Code Register
Exclusive-OR Immediate to
Status Register
Exchange Registers
Sign-Extend
```
###### TAS

###### TBLS, TBLSN

###### TBLU, TBLUN

###### TRAP

```
TRAPcc
TRAPV
TST
```
```
Test Operand and Set
Signed/Unsigned Table Lookup and
Interpolate
Signed/Unsigned Table Lookup and
Interpolate
Trap
Trap Conditionally
Trap an Overflow
Test Operand
ILLEGAL Take Illegal Instruction Trap UNLK Unlink
JMP
JSR
```
```
Jump
Jump to Subroutine
LEA
LINK
LPSTOP
LSL, LSR
```
```
Load Effective Address
Link and Allocate
Low Power Stop
Logical Shift Left and Right
```

##### CPU32 Instructions

##### 7-4

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# BGND

## Enter Background Mode

# BGND

## (CPU32)

#### Operation:

#### If Background Mode Enabled

#### Then Enter Background Mode

#### Else Format/Vector Offset

#### →

- (SSP);

#### PC

#### →

- (SSP)

#### SR

#### →

- (SSP)

#### (Vector)

#### →

#### PC

#### Assembler

#### Syntax:

#### BGND

#### Attributes:

#### Size = (Unsized)

#### Description:

#### The processor suspends instruction execution and enters background mode

#### if background mode is enabled. The freeze output is asserted to acknowledge entrance

#### into background mode. Upon exiting background mode, instruction execution

#### continues with the instruction pointed to by the current program counter. If background

#### mode is not enabled, the processor initiates illegal instruction exception processing.

#### The vector number is generated to reference the illegal instruction exception vector.

#### Refer to the appropriate user’s manual for detailed information on background mode.

#### Condition Codes:

#### X — Not affected.

#### N — Not affected.

#### Z — Not affected.

#### V — Not affected.

#### C — Not affected.

#### Instruction Format:

###### X N Z V C

###### — — — — —

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
0 1 0 0 1 0 1 0 1 1 1 1 1 0 1 0
```

##### CPU32 Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 7-5

# LPSTOP

## Low-Power Stop

# LPSTOP

## (CPU32)

#### Operation:

#### If Supervisor State

#### Immediate Data

#### →

#### SR

#### Interrupt Mask

#### →

#### External Bus Interface (EBI)

#### STOP

#### Else TRAP

#### Assembler

#### Syntax:

#### LPSTOP # < data >

#### Attributes:

#### Size = (Word) Privileged

#### Description:

#### The immediate operand moves into the entire status register, the program

#### counter advances to point to the next instruction, and the processor stops fetching and

#### executing instructions. A CPU LPSTOP broadcast cycle is executed to CPU space $3

#### to copy the updated interrupt mask to the external bus interface (EBI). The internal

#### clocks are stopped.

#### Instruction execution resumes when a trace, interrupt, or reset exception occurs. A

#### trace exception will occur if the trace state is on when the LPSTOP instruction is

#### executed. If an interrupt request is asserted with a higher priority that the current

#### priority level set by the new status register value, an interrupt exception occurs;

#### otherwise, the interrupt request is ignored. If the bit of the immediate data

#### corresponding to the S-bit is off, execution of the instruction will cause a privilege

#### violation. An external reset always initiates reset exception processing.

#### Condition Codes:

#### Set according to the immediate operand.

#### Instruction Format:

#### Instruction Fields:

#### Immediate field—Specifies the data to be loaded into the status register.

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1 1 1 1 1 0 0 0 0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 1 1 1 0 0 0 0 0 0
IMMEDIATE DATA
```

##### CPU32 Instructions

##### 7-6

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# TBLS TBLS

# TBLSN

## Table Lookup and Interpolate (Signed)

# TBLSN

#### (CPU32)

#### Operation:

#### Rounded:

#### ENTRY(n) + {(ENTRY(n + 1) – ENTRY(n)) x Dx 7 – 0}

#### ÷

#### 256

#### →

#### Dx

#### Unrounded:

#### ENTRY(n) x 256 + {(ENTRY(n + 1) – ENTRY(n)) x Dx 7 – 0}

#### →

#### Dx

#### Where ENTRY(n) and ENTRY(n + 1) are either:

#### 1. Consecutive entries in the table pointed to by the < ea > and

#### indexed by Dx 15 – 8

#### π

#### SIZE or;

#### 2. The registers Dym, Dyn respectively.

#### Assembler

#### TBLS. < size > < ea > ,Dx Result rounded

#### Syntax:

#### TBLSN. < size > < ea > ,Dx Result not rounded

#### TBLS. < size > Dym:Dyn, Dx Result rounded

#### TBLSN. < size > Dym:Dyn, Dx Result not rounded

#### Attributes:

#### Size = (Byte, Word, Long)

#### Description:

#### The TBLS and TBLSN instructions allow the efficient use of piecewise linear

#### compressed data tables to model complex functions. The TBLS instruction has two

#### modes of operation: table lookup and interpolate mode and data register interpolate

#### mode.

#### For table lookup and interpolate mode, data register Dx 15 – 0 contains the

#### independent variable X. The effective address points to the start of a signed byte, word,

#### or long-word table containing a linearized representation of the dependent variable, Y,

#### as a function of X. In general, the independent variable, located in the low-order word

#### of Dx, consists of an 8-bit integer part and an 8-bit fractional part. An assumed radix

#### point is located between bits 7 and 8. The integer part, Dx 15 – 8, is scaled by the

#### operand size and is used as an offset into the table. The selected entry in the table is

#### subtracted from the next consecutive entry. A fractional portion of this difference is

#### taken by multiplying by the interpolation fraction, Dx 7 – 0 .The adjusted difference is

#### then added to the selected table entry. The result is returned in the destination data

#### register, Dx.


##### CPU32 Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 7-7

# TBLS TBLS

# TBLSN

## Table Lookup and Interpolate (Signed)

# TBLSN

#### (CPU32)

#### For register interpolate mode, the interpolation occurs using the Dym and Dyn registers

#### in place of the two table entries. For this mode, only the fractional portion, Dx 7 – 0, is

#### used in the interpolation, and the integer portion, Dx 15 – 8, is ignored. The register

#### interpolation mode may be used with several table lookup and interpolations to model

#### multidimensional functions.

#### Signed table entries range from – 2

##### n – 1

#### to 2

##### n – 1

- 1; whereas, unsigned table entries

#### range from 0 to 2

##### n – 1

#### where n is 8, 16, or 32 for byte, word, and long-word tables,

#### respectively.

#### Rounding of the result is optionally selected via the "R" instruction field. If R = 0

#### (TABLE), the fractional portion is rounded according to the round-to-nearest algorithm.

#### The following table summerizes the rounding procedure:

#### The adjusted difference is then added to the selected table entry. The rounded result

#### is returned in the destination data register, Dx. Only the portion of the register

#### corresponding to the selected size is affected.

```
Adjusted Difference
Fraction
```
```
Rounding
Adjustment
≤
```
- 1/2 – 1
> – 1/2 and < 1/2 + 0
≥
1/2 + 1

###### 31 24 23 16 15 8 7 0

###### BYTE UNAFFECTED UNAFFECTED UNAFFECTED RESULT

###### WORD UNAFFECTED UNAFFECTED RESULT RESULT

###### LONG RESULT RESULT RESULT RESULT


##### CPU32 Instructions

##### 7-8

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### MOTOROLA

# TBLS TBLS

# TBLSN

## Table Lookup and Interpolate (Signed)

# TBLSN

#### (CPU32)

#### If R = 1 (TABLENR), the result is returned in register Dx without rounding. If the size is

#### byte, the integer portion of the result is returned in Dx 15 – 8; the integer portion of a

#### word result is stored in Dx 23 – 8; the least significant 24 bits of a long result are stored

#### in Dx 31 – 8. Byte and word results are sign-extended to fill the entire 32-bit register.

#### NOTE

#### The long-word result contains only the least significant 24 bits of

#### integer precision.

#### For all sizes, the 8-bit fractional portion of the result is returned to the low byte of the

#### data register, Dx 7 – 0. User software can make use of the fractional data to reduce

#### cumulative errors in lengthy calculations or implement rounding algorithms different

#### from that provided by other forms of TBLS. The previously described assumed radix

#### point places two restrictions on the programmer:

#### 1. Tables are limited to 257 entries in length.

#### 2. Interpolation resolution is limited to 1/256, the distance between consecutive ta-

#### ble entries. The assumed radix point should not, however, be construed by the

#### programmer as a requirement that the independent variable be calculated as a

#### fractional number in the range 0 <

#### π

#### < 255. On the contrary, X should be consid-

#### ered an integer in the range 0 <

#### π

#### < 65535, realizing that the table is actually a

#### compressed representation of a linearized function in which only every 256th

#### value is actually stored in memory.

###### 31 24 23 16 15 8 7 0

###### BYTE SIGN-EXTENDED SIGN-EXTENDED RESULT FRACTION

###### WORD SIGN-EXTENDED RESULT RESULT FRACTION

###### LONG RESULT RESULT RESULT FRACTION


##### CPU32 Instructions

##### MOTOROLA

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL

##### 7-9

# TBLS TBLS

# TBLSN

## Table Lookup and Interpolate (Signed)

# TBLSN

#### (CPU32)

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if the integer portion of an unrounded long result is not in the range, – (2

##### 23

#### )

#### ≤

#### Result

#### ≤

#### (2

##### 23

#### ) – 1; cleared otherwise.

#### C — Always cleared.

#### Instruction Format:

##### TABLE LOOKUP AND INTERPOLATE

##### DATA REGISTER INTERPOLATE

###### X N Z V C

###### —

###### ∗∗∗

###### 0

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111100000) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Dx 1 R 0 1 SIZE 0 0 0 0 0 0
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111100000000 REGISTER Dym
0 REGISTER Dx 1 R 0 1 SIZE 0 0 0 REGISTER Dyn


##### CPU32 Instructions

##### 7-10

##### M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# TBLS TBLS

# TBLSN Table Lookup and Interpolate (Signed) TBLSN

#### (CPU32)

#### Instruction Fields:

#### Effective address field (table lookup and interpolate mode only)—Specifies the

#### destination location. Only control alterable addressing modes are allowed as listed

#### in the following table:

#### Size Field—Specifies the size of operation.

#### 00 — Byte Operation

#### 01 — Word Operation

#### 10 — Long Operation

#### Register field—Specifies the destination data register, Dx. On entry, the register

#### contains the interpolation fraction and entry number.

#### Dym, Dyn field—If the effective address mode field is nonzero, this operand register is

#### unused and should be zero. If the effective address mode field is zero, the surface

#### interpolation variant of this instruction is implied, and Dyn specifies one of the two

#### source operands.

#### Rounding mode field—The R-bit controls the rounding of the final result. When R = 0,

#### the result is rounded according to the round-to-nearest algorithm. When R = 1, the

#### result is returned unrounded.

```
Addressing Mode Mode Register Addressing Mode Mode Register
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) — — # < data > — —
(An) + — —
```
- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011


##### CPU32 Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 7-11

# TBLU TBLU

# TBLUN Table Lookup and Interpolation (Unsigned) TBLUN

#### (CPU32)

#### Operation: Rounded:

#### ENTRY(n) + {(ENTRY(n + 1) – ENTRY(n)) x Dx 7 – 0} ÷ 256 → Dx

#### Unrounded:

#### ENTRY(n) x 256 + {(ENTRY(n + 1) – ENTRY(n)) x Dx 7 – 0} → Dx

#### Where ENTRY(n) and ENTRY(n + 1) are either:

#### 1. Consecutive entries in the table pointed to by the < ea > and

#### indexed by Dx 15 – 8 π SIZE or;

#### 2. The registers Dym, Dyn respectively

#### Assembler TBLU. < size > < ea > ,Dx Result rounded

#### Syntax: TBLUN. < size > < ea > ,Dx Result not rounded

#### TBLU. < size > Dym:Dyn, Dx Result rounded

#### TBLUN. < size > Dym:Dyn, Dx Result not rounded

#### Attributes: Size = (Byte, Word, Long)

#### Description: The TBLU and TBLUN instructions allow the efficient use of piecewise linear,

#### compressed data tables to model complex functions. The TBLU instruction has two

#### modes of operation: table lookup and interpolate mode and data register interpolate

#### mode.

#### For table lookup and interpolate mode, data register Dx 15 – 0 contains the

#### independent variable X. The effective address points to the start of a unsigned byte,

#### word, or long-word table containing a linearized representation of the dependent

#### variable, Y, as a function of X. In general, the independent variable, located in the low-

#### order word of Dx, consists of an 8-bit integer part and an 8-bit fractional part. An

#### assumed radix point is located between bits 7 and 8. The integer part, Dx 15 – 8, is

#### scaled by the operand size and is used as an offset into the table. The selected entry

#### in the table is subtracted from the next consecutive entry. A fractional portion of this

#### difference is taken by multiplying by the interpolation fraction, Dx 7 – 0. The adjusted

#### difference is then added to the selected table entry. The result is returned in the

#### destination data register, Dx.


##### CPU32 Instructions

##### 7-12 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# TBLU TBLU

# TBLUN Table Lookup and Interpolation (Unsigned) TBLUN

#### (CPU32)

#### For register interpolate mode, the interpolation occurs using the Dym and Dyn registers

#### in place of the two table entries. For this mode, only the fractional portion, Dx 7 – 0, is

#### used in the interpolation and the integer portion, Dx 15 – 8, is ignored. The register

#### interpolation mode may be used with several table lookup and interpolations to model

#### multidimensional functions.

#### Signed table entries range from – 2n – 1 to 2n – 1 – 1; whereas, unsigned table entries

#### range from 0 to 2n – 1 where n is 8, 16, or 32 for byte, word, and long-word tables,

#### respectively. The unsigned and unrounded table results will be zero-extended instead

#### of sign-extended.

#### Rounding of the result is optionally selected via the "R" instruction field. If R = 0

#### (TABLE), the fractional portion is rounded according to the round-to-nearest algorithm.

#### The rounding procedure can be summarized by the following table:

#### The adjusted difference is then added to the selected table entry. The rounded result

#### is returned in the destination data register, Dx. Only the portion of the register

#### corresponding to the selected size is affected.

#### If R = 1 (TBLUN), the result is returned in register Dx without rounding. If the size is

#### byte, the integer portion of the result is returned in Dx 15 – 8; the integer portion of a

#### word result is stored in Dx 23 – 8; the least significant 24 bits of a long result are stored

#### in Dx 31 – 8. Byte and word results are sign-extended to fill the entire 32-bit register.

```
Adjusted Difference
Fraction
```
```
Rounding
Adjustme
nt
≥ 1/2 + 1
< 1/2 + 0
```
###### 31 24 23 16 15 8 7 0

###### BYTE UNAFFECTED UNAFFECTED UNAFFECTED RESULT

###### WORD UNAFFECTED UNAFFECTED RESULT RESULT

###### LONG RESULT RESULT RESULT RESULT


##### CPU32 Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 7-13

# TBLU TBLU

# TBLUN Table Lookup and Interpolation (Unsigned) TBLUN

#### (CPU32)

#### NOTE

#### The long-word result contains only the least significant 24 bits of

#### integer precision.

#### For all sizes, the 8-bit fractional portion of the result is returned in the low byte of the

#### data register, Dx 7 – 0. User software can make use of the fractional data to reduce

#### cumulative errors in lengthy calculations or implement rounding algorithms different

#### from that provided by other forms of TBLU. The previously described assumed radix

#### point places two restrictions on the programmer:

#### 1. Tables are limited to 257 entries in length.

#### 2. Interpolation resolution is limited to 1/256, the distance between consecutive ta-

#### ble entries. The assumed radix point should not, however, be construed by the

#### programmer as a requirement that the independent variable be calculated as a

#### fractional number in the range 0 ≤ X ≤ 255. On the contrary, X should be consid-

#### ered to be an integer in the range 0 ≤ X ≤ 65535, realizing that the table is actu-

#### ally a compressed representation of a linearized function in which only every

#### 256th value is actually stored in memory.

#### Condition Codes:

#### X — Not affected.

#### N — Set if the most significant bit of the result is set; cleared otherwise.

#### Z — Set if the result is zero; cleared otherwise.

#### V — Set if the integer portion of an unrounded long result is not in the range, – (2^23 )

#### ≤ Result ≤ (2^23 ) – 1; cleared otherwise.

#### C — Always cleared.

###### 31 24 23 16 15 8 7 0

###### BYTE SIGN-EXTENDED SIGN-EXTENDED RESULT FRACTION

###### WORD SIGN-EXTENDED RESULT RESULT FRACTION

###### LONG RESULT RESULT RESULT FRACTION

###### X N Z V C

###### — ∗∗∗ 0


##### CPU32 Instructions

##### 7-14 M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL MOTOROLA

# TBLU TBLU

# TBLUN Table Lookup and Interpolation (Unsigned) TBLUN

#### (CPU32)

#### Instruction Format:

##### TABLE LOOKUP AND INTERPOLATE

##### DATA REGISTER INTERPOLATE

#### Instruction Fields:

#### Effective address field (table lookup and interpolate mode only)—Specifies the

#### destination location. Only control alterable addressing modes are allowed as listed

#### in the following table:

#### Size field—Specifies the size of operation.

#### 00 — Byte Operation

#### 01 — Word Operation

#### 10 — Long Operation

```
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
```
(^1111100000) MODEEFFECTIVE ADDRESS REGISTER
0 REGISTER Dx 0 R 0 1 SIZE 0 0 0 0 0 0 0
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
1111100000000 REGISTER Dym
0 REGISTER Dx 0 R 0 0 SIZE 0 0 0 REGISTER Dyn
**Addressing Mode Mode Register Addressing Mode Mode Register**
Dn — — (xxx).W 111 000
An — — (xxx).L 111 001
(An) 010 reg. number:An # < data > — —
(An) + — —

- (An) 100 reg. number:An
(d 16 ,An) 101 reg. number:An (d 16 ,PC) 111 010
(d 8 ,An,Xn) 110 reg. number:An (d 8 ,PC,Xn) 111 011
(bd,An,Xn) 110 reg. number:An (bd,PC,Xn) 111 011


##### CPU32 Instructions

##### MOTOROLA M68000 FAMILY PROGRAMMER’S REFERENCE MANUAL 7-15

# TBLU TBLU

# TBLUN Table Lookup and Interpolation (Unsigned) TBLUN

#### (CPU32)

#### Register field—Specifies the destination data register, Dx. On entry, the register

#### contains the interpolation fraction and entry number.

#### Dym, Dyn field—If the effective address mode field is nonzero, this operand register is

#### unused and should be zero. If the effective address mode field is zero, the surface

#### interpolation variant of this instruction is implied, and Dyn specifies one of the two

#### source operands.

#### Rounding mode field—The R-bit controls the rounding of the final result. When R = 0,

#### the result is rounded according to the round-to-nearest algorithm. When R = 1,

#### the result is returned unrounded.


