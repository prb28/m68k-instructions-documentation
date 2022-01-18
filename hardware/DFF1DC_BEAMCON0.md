**Beam Counter Control Bits**

|Bit| Function  |
|---|---  |
|15| Unused  |
|14| HARDDIS  |
|13| LPENDIS  |
|12| VARVBEN  |
|11| LOLDIS  |
|10| CSCBEN  |
|9| VARVSYEN  |
|8| VARHSYEN  |
|7| VARBEAMEN  |
|6| DUAL  |
|5| PAL  |
|4| VARCSYEN  |
|3| (unused, formerly BLANKEN)  |
|2| CSYTRUE  |
|1| VSYTRUE  |
|0| HSYTRUE|

**HARDDIS** This bit is used to disable the hardwired vertical horizontal window limits. It is cleared upon reset. **LPENDIS** **LPENDIS** When this bit is a low and LPE ([BPLCON0](DFF100_BPLCON0.md), bit 3) is enabled, the light-pen latched value(beam hit position) will be read by [VHPOSR](DFF006_VHPOSR.md), [VPOSR](DFF004_VPOSR.md) and [HHPOSR](DFF1D8_HHPOSW.md). When the bit is a high the light-pen latched value is ignored and the actual beam counter position is read by [VHPOSR](DFF006_VHPOSR.md), [VPOSR](DFF004_VPOSR.md), and [HHPOSR](DFF1D8_HHPOSW.md). **VARVBEN** **VARVBEN** Use the comparator generated vertical blank (from [VBSTRT](DFF1CC_VBSTRT.md), [VBSTOP](DFF1CC_VBSTRT.md)) to run the internal chip stuff-sending RGA signals to Denise, starting sprites,resetting light pen. It also disables the hard stop on the vertical display window. **LOLDIS** **LOLDIS** Disable long line/short toggle. This is useful for DUAL mode where even multiples are wanted, or in any single display where this toggling is not desired. **CSCBEN** **CSCBEN** The variable composite sync comes out on the HSY pin, and the variable composite blank comes out on the VSY pin. The idea is to allow all the information to come out of the chip for a DUAL mode display. The normal monitor uses the normal composite sync, and the variable composite sync  &blank come out the HSY & VSY pins. The bits VARVSTEN & VARHSYEN (below) have priority over this control bit. **VARVSYEN** **VARVSYEN** Comparator VSY - > VSY pin. The variable VSY is set vertically on [VSSTRT](DFF1E0_VSSTRT.md), reset vertically on [VSSTOP](DFF1C8_VTOTAL.md), with the horizontal position for set set & reset [HSSTRT](DFF1DE_HSSTRT.md) on short fields (all fields are short if LACE = 0) and [HCENTER](DFF1E2_HCENTER.md) on long fields (every other field if LACE = 1). **VARHSYEN** **VARHSYEN** Comparator HSY - > HSY pin. Set on [HSSTRT](DFF1DE_HSSTRT.md) value, reset on [HSSTOP](DFF1DE_HSSTRT.md) value. **VARBEAMEN** **VARBEAMEN** Enables the variable beam counter comparators to operate (allowing different beam counter total values) on the main horiz counter. It also disables hard display stops on both horizontal and vertical. **DUAL** **DUAL** Run the horizontal comparators with the alternate horizontal beam counter, and starts the UHRES pointer chain with the reset of this counter rather than the normal one. This allows the UHRES pointers to come out more than once in a horizontal line, assuming there is some memory bandwidth left (it doesn't work in 640*400*4 interlace mode) also, to keep the two displays synced, the horizontal line lengths should be multiples of each other. If you are amazingly clever, you might not need to do this. **PAL** **PAL** Set appropriate decodes (in normal mode) for PAL. In variable beam counter mode this bit disables the long line/short line toggle- ends up short line. **VARCSYEN** **VARCSYEN** Enables CSY from the variable decoders to come out the CSY (VARCSY is set on [HSSTRT](DFF1DE_HSSTRT.md) match always, and also on [HCENTER](DFF1E2_HCENTER.md) match when in vertical sync. It is reset on [HSSTOP](DFF1C2_HSSTOP.md) match when VSY and on both [HBSTRT](DFF1C4_HBSTRT.md) & [HBSTOP](DFF1C4_HBSTRT.md) matches during VSY. A reasonable composite can be generated by setting [HCENTER](DFF1E2_HCENTER.md) half a horizontal line from [HSSTRT](DFF1DE_HSSTRT.md), and [HBSTOP](DFF1C4_HBSTRT.md) at ([HSSTOP](DFF1C2_HSSTOP.md)-[HSSTRT](DFF1DE_HSSTRT.md)) before [HCENTER](DFF1E2_HCENTER.md), with [HBSTRT](DFF1C4_HBSTRT.md) at ( [HSSTOP](DFF1C2_HSSTOP.md)-[HSSTRT](DFF1DE_HSSTRT.md)) before [HSSTRT](DFF1DE_HSSTRT.md). **HSYTRUE, VSYTRUE, CSYTRUE** **HSYTRUE, VSYTRUE, CSYTRUE** These change the polarity of the HSY*, VSY*,  & CSY* pins to HSY, VSY, & CSY respectively for input and output.
