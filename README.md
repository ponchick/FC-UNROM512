# FC-UNROM512

UNROM512 NES/Famicom cartridge PCB (UNROM/UOROM family, extended PRG-ROM bank switching).

Russian version: [`README.ru.md`](README.ru.md)

More details about UNROM512 format and compatibility:

- [NESdev Wiki - UNROM 512](https://www.nesdev.org/wiki/UNROM_512)
- [NESdev Wiki mirror - UNROM 512](https://nesdev-wiki.nes.science/wikipages/UNROM_512.xhtml)

---

## Jumpers (board configuration)

### 1) Flash memory mode (write protection / self-flashing)

| Configuration | `FLASHLOCKED1`-`FLASHLOCKED4` | `FLASHABLE` | 74*139 | Bus conflicts |
| :--- | :---: | :---: | :---: | :---: |
| **Not Flashable** (write-protected) | Closed | Open | Not installed | **Present** |
| **Flashable** (self-flashable) | Open | Closed | Installed | **Absent** |

---

### 2) Mirroring

**Mirroring must match the ROM you are programming.** The game expects a specific mode (vertical/horizontal/1-screen). A wrong setting causes visual glitches.

Possible jumper states:

- **Vertical mirroring:** `VERTICAL` closed, `HORIZONTAL` and `ONE` open.
- **Horizontal mirroring:** `HORIZONTAL` closed, `VERTICAL` and `ONE` open.
- **1-screen mirroring (mapper-controlled):** `ONE` closed, `VERTICAL` and `HORIZONTAL` open.

---

### 3) CHR RAM size configuration (8/16/32 KiB)

**The actual CHR RAM size is defined by the physical RAM chip** (for example, 62256 = 32 KiB). Jumpers only route the required address lines.

| Size | `CHR RAM 8k` | `CHR RAM 8k/16k` | `CHR RAM 16k/32k` | `CHR RAM 32k` |
| :--- | :---: | :---: | :---: | :---: |
| 8 KiB | Closed | Closed | Closed | Open |
| 16 KiB | Closed | Closed | Open | Open |
| 32 KiB | Open | Closed | Closed | Open |

> **Use smaller CHR RAM sizes (8/16 KiB) only if the target ROM explicitly supports them.** Most UNROM512 / Mapper 30 software expects 32 KiB. Forcing a smaller size on unsupported ROMs can cause errors.

---

## License

This project is licensed under CERN Open Hardware Licence Version 2 - Permissive (`CERN-OHL-P-2.0`), see `LICENSE`.

SPDX-License-Identifier: `CERN-OHL-P-2.0`
