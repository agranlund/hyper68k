# Hyper68k
## 68000 virtual machine library for 68030

Library source and api header lives under [src/h68k/](src/h68k) 

Guest 68000 system runs in 68030 usermode and with virtualised super + usermode.

Library takes care of privileged instruction emulation, virtualized address map, and translationg of exception frame differences between the two CPU models.

It alos provides an API allowing an application to easily customize the guest address map, marking ranges for translation, access error, direct passthrough or for getting a callback to application to perform peripheral emulation.

- [src/h68k/h68k.h](src/h68k/h68k.h) - application API
- [src/h68k/h68k.c](src/h68k/h68k.c) - application API
- [src/h68k/mmu.c](src/h68k/mmu.c) - internal pmmu utility functions
- [src/h68k/vec.c](src/h68k/vec.c) - internal vbr utility functions
- [src/h68k/xberr.S](src/h68k/xberr.S) - PMMU exception handler, translation, and app callbacks for IO emulation
- [src/h68k/xpviol.S](src/h68k/xpviol.S) - privileged instruction emulation
- [src/h68k/xvec.S](src/h68k/xvec.S) - guest exception handling and stackframe translation



## Example / Testbed application
A small testbed application which uses the library lives directly in [src/](src)

It uses the library to be able to run TOS 1.x + applications on a 68030 system. Something which would normally not be possible directly.
This application should not be considered an actual end product. It was merely the testbed application to have a solid use-case when working on the library. It is neither polished nor a fully featured thing.

Licensed under GPL2, see license.txt.

-- Anders Granlund, 2024
