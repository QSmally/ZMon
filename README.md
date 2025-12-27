
# ZMon

Wozmon (written by Steve Wozniak in 1976) created for the Z80 and Z80-family of peripherals.

The ZMon hex monitor runs in EEPROM (16k) space from address `0x0000`. The input buffer is placed in
RAM (48k) at `0x4000` to `0x407F`, with one additional word necessary (`0x4080`, `0x4081`). The
stack is initialised to the top of RAM at `0xFFFF`.

The monitor uses UART over the SIO peripheral; 8 bits, 1 stop bit, no parity, 9600 baud.

I/O mapping is as follows:

- `0xC0` - SIO (Serial Input/Output)
- `0xE0` - CTC (Counter/Timer Circuit)

![](./output.png)

## Contributing

I use [Vasm](http://www.compilers.de/vasm.html) oldstyle to assemble this project.

Currently, given that the SIO needs a lot of initialisation instructions, the binary is around 300
bytes long. I'm willing to accept any kind of space optimisations anybody can come up with. I
haven't tried too much yet and I tried keeping it 1:1 without weird branch dependencies.
