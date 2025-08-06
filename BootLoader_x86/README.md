GNU GRUB (short for GNU GRand Unified Bootloader, commonly referred to as GRUB) is a boot loader package from the GNU Project.

x86 sys specs

| Component               | Details                                                                |
| ----------------------- | ---------------------------------------------------------------------- |
| **CPU Architecture**    | x86 (Intel 8086/8088/80286 and upward)                                 |
| **Data Bus**            | 16-bit (in 8086); later extended in 32-bit and 64-bit processors       |
| **Address Bus**         | 20-bit (in Real Mode) → can address **1 MB** (2²⁰ = 1,048,576 bytes)   |
| **Registers**           | 16-bit general purpose: AX, BX, CX, DX, SI, DI, BP, SP                 |
|                         | 16-bit segment: CS, DS, SS, ES, FS, GS                                 |
| **Instruction Pointer** | 16-bit (`IP`)                                                          |
| **Stack**               | Located via `SS:SP`                                                    |
| **Memory Addressing**   | `segment:offset` → 20-bit physical address                             |
| **Clock Speed**         | \~4.77 MHz (8086); higher in later x86 CPUs                            |
| **I/O**                 | Handled via `IN` and `OUT` instructions (I/O ports, not memory-mapped) |
| **Interrupts**          | 256 interrupt vectors (`INT 0x00` to `INT 0xFF`) in IVT                |
| **BIOS**                | Present at top of memory (`0xF0000 – 0xFFFFF`)                         |
| **Video Memory**        | Typically starts at `0xB8000` for text-mode (VGA)                      |
| **Boot Process**        | Begins at `0x7C00` (where BIOS loads the boot sector)                  |


When you turn your computer on, the processor immediately looks at physical address 0xFFFFFFF0 for the BIOS code, which is generally on some read-only piece of ROM somewhere in your computer. The BIOS then POSTs, and searches for acceptable boot media. The BIOS accepts some medium as an acceptable boot device if its boot sector, the first 512 bytes of the disk are readable and end in the exact bytes 0x55AA, which constitutes the boot signature for the medium. If the BIOS deems some drive bootable, then it loads the first 512 bytes of the drive into memory address 0x007C00.

First, MRB is located MRB points to another boot sector which usually loads the kernel. This is called chain loading.

In x86 Real Mode, memory is addressed using a formula:

Physical Address = (Segment × 0x10) + Offset

Segment and Offset are both 16-bit values (0–65535)

Max physical address = 0xFFFF0 + 0xFFFF = 0x10FFEF → Just over 1 MB

The base address of a segment is the (A * 0x10) portion of the equation I showed. It should be obvious that segments can overlap.

Eg, the segment 0x1000 has a base address of 0x10000. This segment occupies the physical address range 0x10000 -> 0x1FFFF, However the segment 0x1010 has a base address of 0x10100. This segment occupies the physical address range 0x10100 -> 0x200FF

As you can see we could use either segment to reach physical addresses between 0x10100 and 0x1FFFF since the segments overlap.

The x86 line of computers have 6 segment registers (CS, DS, ES, FS, GS, SS). They are totally independent of one another.

The Netwide Assembler (NASM) is an assembler and disassembler for the Intel x86 architecture.

Bochs (pronounced "box") is a portable IA-32 and x86-64 IBM PC compatible emulator and debugger mostly written in C++ and distributed as free software under the GNU Lesser General Public License. It supports emulation of the processor(s) (including protected mode), memory, disks, display, Ethernet, BIOS and common hardware peripherals of PCs.



** To be Continued.. **
