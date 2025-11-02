# IBM 4694 Point of Sale (POS)
The IBM 4694 is a family of Point of Sale (POS) terminals designed by IBM for retail environments. Characterized by high reliability, specialized hardware, and a proprietary operating system.

## System Specifications
- IBM 4694 PoS (Point of Sale) system
- Motherboard: FRU 85H4990 - 4694-104
- CPU = AMD 5x86 100MHz
- VGA = Cirrus Logic CL-GD543x

### Specialized Operating System (IBM 4690 OS)
- The 4690 OS uses a **proprietary, transaction-based file system** for data integrity.

### Peripheral Integration
- The board includes direct headers for POS-specific peripherals like cash drawers, barcode scanners, and magnetic stripe readers (MSR).

## Bios 
The IBM 4694 does not use a conventional BIOS. Instead, it uses a two-stage **Initial Machine Load (IML)** process:
- A small boot code in the onboard EEPROM (`Intel P28F001BX-T`) performs initial hardware checks.
- The main system POST and BIOS code (the "IML image") is loaded from a **hidden system partition on the HDD**.
- This ensures the hardware and software are a matched set, enhancing security and reliability.
- Segment1: 0x0000 - 0x7FFF   (Video BIOS)
- Segment2: 0x8000 - 0x10000 (Network boot ROM)
- Segment3: 0x10000 - END    (System BIOS)

### Factory 
- `The IBM_4964_85H4990_BIOS.bin` file is the original BIOS image extracted from the EEPROM.

### Custom version 
- `IBM_4964_85H4990_XTIDE_CUSTOM_BIOS.bin` This version leaves Segment1 and Segement3 of the original BIOS intact but replaces Segment2 with the custom XTIDE Universal BIOS code.
- This hybrid approach allows the proprietary IBM BIOS to initialize the core hardware, after which the XTIDE code takes over to enable booting from a custom HDD. This bypasses the system's default requirement for a proprietary IBM hard drive.