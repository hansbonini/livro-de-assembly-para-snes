# Changing the processor flags
As you saw in the "8-bit and 16-bit mode" chapter earlier, the SNES can switch between 8-bit and 16-bit mode by using the opcodes REP and SEP. These affect the processor flags, which affects the behaviour of the SNES. Two of the prcoessor flags are dedicated to A and X & Y being 8-bit or 16-bit mode. There are in total 8 processor flags stored in the processor flags register as a single byte:

![](../.gitbook/assets/processorflags.png)

|Opcode|Full name|Explanation|
|-|-|-|
|**REP**|Reset processor flags|Sets specified processor flags to 0|
|**SEP**|Set processor flags|Sets specified processor flags to 1|

SEP sets the selected bits to 1 while REP resets the selected bits to 0. They work pretty much like TSB and TRB from the bitwise operations chapter, except these opcodes affect the SNES processor flags instead.

In the image, m and x are described as "Index Register/Memory/Accumulator select". The index register is in fact the X and Y 8-bit or 16-bit mode register, while the memory/accumulator select is the same, just for the accumulator.

## SEP
SEP works as following:
```
;nvmxdizc = 0000 0000
SEP #$80 ;= 1000 0000
;Nvmxdizc = 1000 0000
```
The uppercased letters are the activated processor flags. This code sets the negative flag.

## REP
REP works as following:
```
;NvmxDizc = 1000 1000
REP #$08 ;= 0000 1000
;Nvmxdizc = 1000 0000
```
In the beginning, the decimal mode was enabled, and the negative flag was set, but after `REP #$08`, the decimal mode flag got disabled and the negative flag is still set.

## XCE and the emulation mode
You might be wondering why that green `e` is in that image at such a peculiar position.

It is the ‘hidden’ emulation mode of the SNES. When it is set, SNES basically acts like 6502 (NES CPU), which is far more limited. While in emulation mode, the accumulator, X and Y register are forced to be 8-bit and one of the processor flag is used to indicate BRK. It also uses different vectors for interrupt. You can’t set the emulation mode using REP and SEP. Emulation mode is basically an ‘improved’ 6502 processor emulation.

|Opcode|Full name|Explanation|
|-|-|-|
|**XCE**|Exchange carry and emulation|Swaps the values of carry flag and emulation mode flag|
You can access the Emulation Mode by using `SEC` then `XCE`, and leave it using `CLC` then `XCE`. By default, SNES starts up in emulation mode. This is why you often see the opcodes `CLC` and `XCE` among the very first opcodes in disassemblies.