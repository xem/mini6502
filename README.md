mini6502
========

An attempt to make the smallest standalone NES CPU (Ricoh 6502) simulator in JavaScript (< 1kb zipped)

Developed for my mini NES emulator: https://github.com/xem/jsnes-lite

A writeup is available on: https://xem.github.io/articles/nes.html

Commented source code: https://github.com/xem/mini6502/blob/gh-pages/6502.js

Minified: https://github.com/xem/mini6502/blob/gh-pages/6502.min.js

Zipped: https://github.com/xem/mini6502/blob/gh-pages/6502.min.js.zip (1015b)

Gzipped: https://github.com/xem/mini6502/blob/gh-pages/6502.min.js.gz (928b)

Demo/test: https://xem.github.io/mini6502/demo

<br>
<br>

Features:

- Initialization of memory (m), registers (A, X, Y, S, PC, P), flags (C, Z, I, D, B, V, N) and cycle counter (c) as global vars
- Memory helpers (read: `r(addr)`, write: `w(addr,value)`, push: `h(value)`, pop: `g()`)
- Emulation of the 151 official 6502 opcodes and 3 interrupts
- Emulation of the hardware bugs and quirks (JMP, cross-page reads...)
- Cycle-accurate
- Optimized to run properly at 1.76M cycles/second

<br>
<br>

Features not included:

- NES specific memory mirrorings (showing the same data at different addresses)
- NES specific I/O registers (to handle graphics, sound, joypads...)
- NES Mappers (cartridge models, allowing ROM bank switching, save slots, ...)
- Decimal mode (which is present on the original MOS 6502 CPU but not in Ricoh 6502 used by the NES)

<br>
<br>

How to use:

- Include 6502.js or 6502.min.js in your project
- Put the contents of a ROM in the memory m (an array of integers between 0 and 255) 
- Reset the CPU with `op(2)` or set PC at the address where the program starts
- Call `op()` repeatedly to simulate opcodes one by one
- Call `op(1)` for a NMI interrupt, `op(2)` for a Reset and `op(3)` for an IRQ

<br>
<br>

How to compress after golfing:

- zip: add 6502.min.js in a zip file, run `./ect-0.8.3.exe -9 -zip .\6502.min.zip`
- gzip: run `zopfli --gzip -i1000000 6502.min.js`
- reshuffle opcode list: `<in.txt npx --node-args --experimental-modules dict-tempering --type=newline >out.txt`

<br>
<br>

Useful resources:
- https://wiki.nesdev.com/w/index.php/CPU_unofficial_opcodes
- https://wiki.nesdev.com/w/index.php/Status_flags
- http://wiki.nesdev.com/w/index.php/CPU_interrupts
- https://wiki.nesdev.com/w/index.php/Stack
- https://www.masswerk.at/6502/6502_instruction_set.html
- https://problemkaputt.de/everynes.htm#cpu65xxmicroprocessor
- https://www.npmjs.com/package/dict-tempering
- http://www.6502.org/tutorials/vflag.html
- https://retrocomputing.stackexchange.com/questions/145
- http://forum.6502.org/viewtopic.php?f=8&t=6370
- https://twitter.com/subzey/status/1326227026076971008
- https://twitter.com/subzey/status/1328659977150623750
- https://twitter.com/subzey/status/1328449127471083520
