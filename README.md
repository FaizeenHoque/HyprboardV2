# HyprboardV2

> The RP2040-based dev board that actually got finished — unlike its predecessor.

HyprboardV2 is a compact, RP2040-based development board and the completed successor to the original HyprboardV1 (which never saw the light of day). Built for makers who want a capable, open-source board without the corporate overhead.

---

## Schematic

![Schematic](https://stasis.hackclub-assets.com/images/1772831681282-xnd50o.png)

---

## PCB

<img width="352" height="591" alt="image" src="https://github.com/user-attachments/assets/19c777e5-ef37-40b1-9531-79cc9fdc86ea" />

---

## Renders

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dd50d008-5c01-4d63-9dc6-1427fbf1e1d9" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1ce6cec0-2621-4fff-8176-df455321201c" />

---

# Bill of Materials (BOM)

Manufactured by [JLCPCB](https://jlcpcb.com) · PCB Qty: 5 · Est. Total: **$51.7** (+ PCBA)

> Parts marked **Extended** may incur an additional setup fee at JLCPCB.  
> Headers (J2, J3, J4) are through-hole and excluded from SMT assembly — solder manually.

---

## Passives

| Designator | Value | Footprint | JLCPCB # | Qty | Type |
|---|---|---|---|---|---|
| C1, C2–C9, C11, C12, C17 | 100nF | 0402 | [C1525](https://jlcpcb.com/partdetail/1877-CL05B104KO5NNNC/C1525) | 60 | Basic |
| C10 | 1µF | 0402 | [C52923](https://jlcpcb.com/partdetail/53938-CL05A105KA5NQNC/C52923) | 5 | Basic |
| C13, C14 | 10µF | 0603 | [C19702](https://jlcpcb.com/partdetail/20411-CL10A106KP8NNNC/C19702) | 10 | Basic |
| C15, C16 | 33pF | 0603 | [C1663](https://jlcpcb.com/partdetail/2015-CL10C330JB8NNNC/C1663) | 10 | Basic |
| R1, R2 | 5.1kΩ | 0402 | [C25905](https://jlcpcb.com/partdetail/26648-0402WGF5101TCE/C25905) | 10 | Basic |
| R3, R4 | 27Ω | 0402 | [C25100](https://jlcpcb.com/partdetail/25843-0402WGF270JTCE/C25100) | 22 | Extended |
| R5, R6 | 1kΩ | 0402 | [C11702](https://jlcpcb.com/partdetail/12256-0402WGF1001TCE/C11702) | 10 | Basic |
| R7 | 10kΩ | 0402 | [C25744](https://jlcpcb.com/partdetail/26487-0402WGF1002TCE/C25744) | 5 | Basic |

## ICs & Active Components

| Designator | Part | Package | JLCPCB # | Qty | Type |
|---|---|---|---|---|---|
| U1 | RP2040 | QFN-56 (7×7mm) | [C2040](https://jlcpcb.com/partdetail/RaspberryPi-RP2040/C2040) | 5 | Extended |
| U2 | MCP1700T-3302E/TT (3.3V LDO) | SOT-23 | [C39051](https://jlcpcb.com/partdetail/MicrochipTech-MCP1700T_3302ETT/C39051) | 5 | Extended |
| U4 | W25Q16JVUXIQ (16Mbit Flash) | USON-8 (2×3mm) | [C2843335](https://jlcpcb.com/partdetail/WinbondElec-W25Q16JVUXIQ/C2843335) | 5 | Extended |
| Y1 | 12MHz Crystal | SMD 3225-4P | [C481407](https://jlcpcb.com/partdetail/NDK-NX3225GA_12MHZ_STD_CRG2/C481407) | 5 | Extended |

## Connectors & Switches

| Designator | Part | Package | JLCPCB # | Qty | Type | Notes |
|---|---|---|---|---|---|---|
| J1 | USB-C Receptacle (USB 2.0, 14P) | SMD Right-Angle | [C165948](https://jlcpcb.com/partdetail/Korean_HropartsElec-TYPE_C_31_M12/C165948) | 5 | Extended | |
| J2, J3 | 1×20 Pin Header, 2.54mm | Through-hole | [C50981](https://jlcpcb.com/partdetail/51993-2_54_1_20P/C50981) | — | Extended | **Solder manually** |
| J4 | 1×3 Pin Header, 2.54mm | Through-hole | [C49257](https://jlcpcb.com/partdetail/50265-2_54_1_3P/C49257) | — | Extended | **Solder manually** |
| SW1 | Tactile Switch, SPST-NO | SMD 4×3mm | [C720477](https://jlcpcb.com/partdetail/XUNPU-TS_1088AR02016/C720477) | 5 | Basic | |

---

## Getting Started

### Flashing Firmware

The Hyprboard V2 uses the **RP2040** microcontroller. It supports the
**Raspberry Pi Pico SDK**, **MicroPython**, and **CircuitPython**.

#### Entering Bootloader Mode (BOOTSEL)

The board has one button (SW1) which serves as the BOOTSEL button.

1. Hold **SW1**
2. Plug in USB-C
3. Release **SW1**
4. The board will appear as a USB drive called `RPI-RP2`
5. Drag and drop your `.uf2` firmware file onto it
6. The board reboots and runs your firmware automatically

#### Toolchain Options

| Option | Best For | Link |
|---|---|---|
| Pico SDK (C/C++) | Performance, low-level control | [Getting Started Guide](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) |
| MicroPython | Rapid prototyping | [micropython.org](https://micropython.org/download/RPI_PICO/) |
| CircuitPython | Beginner friendly | [circuitpython.org](https://circuitpython.org/board/raspberry_pi_pico/) |

### Hardware Notes

- **Flash:** 16Mbit (2MB) W25Q16 external flash via QSPI
- **Crystal:** 12MHz — configure your SDK clock accordingly
- **Power:** 3.3V via MCP1700T LDO, input from USB-C (5V)
- **USB:** USB 2.0 Full Speed via USB-C (J1)

---

## Notes

- **R3, R4 (27Ω):** USB D+/D− series resistors. Value is correct per RP2040 hardware design guide.
- **U4 Flash mismatch:** BOM specifies `W25Q16JVZPIQTR`; JLCPCB substituted `W25Q16JVUXIQ` (same die, different package variant — USON-8 vs WSON-8). Verify footprint compatibility before ordering.
- **C1 warning:** JLCPCB flags comment mismatch (part number vs value). This is cosmetic — the part is correct.
- Re-match BOM on JLCPCB if more than 24 hours have passed since last match, as stock and pricing change.

---

## 📜 License

Hardware licensed under [CERN-OHL-P v2](https://ohwr.org/cern_ohl_p_v2.txt)

---

## 🙏 Acknowledgements

Inspired by the failure that was HyprboardV1. Thanks for nothing, V1.
