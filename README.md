# CHIP-8 Test Suite Trace Logs

This repository contains trace logs for [Cadmium](https://github/gulrak/cadmium) runs of the test programs in
Timendus [CHIP-8 test suite](https://github.com/Timendus/chip8-test-suite).

The format of a line is:
```
<instruction-count>/<cycle-count>: <registers-v0-vf> <index-register-i> <program-counter-pc> <opcode-of-next-instruction>  
```
Example:
```
2474/4252: V0:40 V1:40 V2:40 V3:00 V4:74 V5:58 V6:64 V7:84 V8:00 V9:58 VA:70 VB:3c VC:74 VD:32 VE:1a VF:00 I:082d SP:2 PC:0304 O:f01e
```

The trace logs also contain ASCII screen dumps of the screen every time a draw or erase operation takes place, to help
finding the situation interesting to debug a specific problem.

Only the quirk test shows the time handling events in the log as it is irrelevant for the other tests.

**Note:** Also there is not only one way to implement display quirks, the quirks trace has them enabled for classic
CHIP-8 and SCHIP legacy and the way Cadmium does it for the test runs is the most common, where `Dxyn` will keep the PC
at the place until it detects the beginning of a new screen (in this case after the time handler ran) and then will do
the drawing. The exact number of waited opcodes is depending on the concrete way of waiting and the instructions per
frame rate, so an emulate doesn't need to match the trace line by line, but the register contents at the lines that they
share should be the same.



