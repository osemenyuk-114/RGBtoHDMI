# RGBtoHDMI Hardware Variations & Replicas

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![KiCad](https://img.shields.io/badge/Made%20with-KiCad-5C2D91?logo=kicad)](https://www.kicad.org/)
[![Open Source Hardware](https://img.shields.io/badge/Open%20Hardware-OSHW-orange.svg)](https://www.oshwa.org/)

This repository contains fully open-source hardware designs, KiCad schematics, PCB layouts, manufacturing files, and Bills of Materials (BOM) for the **RGBtoHDMI** ecosystem.

**RGBtoHDMI** converts pixel-synchronous digital and analog video from vintage computers (Commodore Amiga, Atari ST, BBC Micro, Commodore 64/128, Sinclair ZX Spectrum, IBM PC MDA/CGA/EGA, Apple II, etc.) to clean HDMI using a Raspberry Pi Zero, custom bare-metal firmware, and a CPLD.

---

## 📋 Included Board Designs

### 1. CPLD Hat V6a (12-Bit Digital RGB Interface)
- **Hybrid V4/V6 Architecture:** Combines the compact design of V6 with enhanced physical durability.
- **SMD Resistor Arrays:** Uses compact `0603 x 4` convex resistor arrays (RN1–RN8) instead of the bulky through-hole arrays from the upstream V4 design.
- **Rugged THT Tactile Switches:** Uses standard 6 mm through-hole tactile pushbuttons (**Alps Alpine SKHHBVA010**) instead of SMD buttons. The small surface-mount pads on commercial V6 boards frequently tear off under repeated button presses during on-screen menu navigation; THT switches eliminate this issue.
- **Automatic CPLD Programming:** The onboard Xilinx **XC9572XL-VQFP44** CPLD is automatically programmed directly by the Raspberry Pi bare-metal firmware upon boot—no separate JTAG programmer or manual intervention is required.
- **Quick Links:** [Schematic (PDF)](Kicad_6Bit/v6a/rgb-to-hdmi.pdf) · [Interactive BOM](Kicad_6Bit/v6a/bom/ibom.html) · [Fabrication Files](Kicad_6Bit/v6a/manufacturing/)

### 2. HDMI Audio Adapter V2a (Audio Add-on Replica)
- **100% Open Hardware Clean-Room Reverse Engineering:** The audio add-on was previously only distributed as closed commercial hardware without public schematics or Gerber files. This replica brings the hardware back into the open-source community. See also the related [RGBtoHDMI Open Audio project](https://github.com/drdpj/RGBtoHDMI-Open-Audio).
- **Audio Digitization:** Based on the Texas Instruments **PCM1808PWR** 24-bit 96 kHz stereo audio ADC, a low-jitter **12.288 MHz** crystal oscillator, and 74LVC logic.
- **Plug-and-Play:** Stacks directly onto header `P2` of the CPLD Hat to feed digital I2S audio into the Raspberry Pi Zero for embedding into the HDMI stream.
- **Quick Links:** [Schematic (PDF)](Kicad_Audio_Adapter/v2a/rgbtohdmi-audio.pdf) · [Interactive BOM](Kicad_Audio_Adapter/v2a/bom/ibom.html) · [Fabrication Files](Kicad_Audio_Adapter/v2a/manufacturing/)

### 3. Analog Board V3a (Analog RGB/YUV Add-on)
- **Cost-Optimized Design:** Compared with the upstream [V3 analog board](https://github.com/IanSB/RGBtoHDMI/tree/master/kicad_analog_6bit/V3), this revision replaces the expensive and hard-to-source `MAX9144` quad comparators with accessible, cost-effective `TC75W57FU` dual comparators.
- **Intended Use:** Designed for video sources with a limited number of analog RGB/YUV levels or monochrome composite video (not intended for full-range analog RGB).
- **Quick Links:** [Schematic (PDF)](Kicad_Analog_6bit/V3a/analog.pdf) · [Interactive BOM](Kicad_Analog_6bit/V3a/bom/ibom.html) · [Fabrication Files](Kicad_Analog_6bit/V3a/manufacturing/)

---

## 🏭 PCB Fabrication Guide (JLCPCB / PCBWay)

Pre-generated, verified manufacturing files (Gerbers and Excellon drill files) are available in each board's `manufacturing/` directory.

To order:
1. Zip the files in the respective board's `manufacturing/` directory.
2. Upload the `.zip` archive to your preferred PCB fabricator (e.g., JLCPCB, PCBWay, OSH Park).
3. Recommended fabrication settings:

| Parameter | Recommended Specification |
| :--- | :--- |
| **Layers** | 2 Layers |
| **Base Material** | Standard FR4 |
| **PCB Thickness** | 1.6 mm |
| **Copper Weight** | 1 oz (35 µm) |
| **Surface Finish** | **ENIG** (recommended for fine-pitch packages: PCM1808 TSSOP-14, XC9572XL VQFP-44) or **Lead-Free HASL** |
| **Solder Mask** | Green (or preferred color) |
| **Silkscreen** | White |
| **Min Track / Spacing** | 6 / 6 mil |

---

## 📖 Software & Documentation

- **Firmware & Releases:** Download pre-built SD card images from the [upstream RGBtoHDMI Releases](https://github.com/IanSB/RGBtoHDMI/releases).
- **User Guide & Wiki:** Comprehensive documentation, configuration instructions, cabling guides, and supported computer profiles can be found on the [official upstream RGBtoHDMI Wiki](https://github.com/IanSB/RGBtoHDMI/wiki).
- **Audio Configuration:** In the RGBtoHDMI on-screen menu, navigate to the audio settings menu to enable HDMI audio embedding.
- **Upstream Sourcing Info:** See upstream [12-bit board BOM](https://github.com/IanSB/RGBtoHDMI/wiki/Bill-of-Materials-%2812-Bit-Board) and [HDMI Audio documentation](https://github.com/IanSB/RGBtoHDMI/wiki/Audio).

---

## 🔍 Interactive BOMs

Interactive HTML assembly guides allow you to easily highlight component placements and trace pads in your web browser:
- 🔗 **CPLD Hat V6a:** [Kicad_6Bit/v6a/bom/ibom.html](Kicad_6Bit/v6a/bom/ibom.html)
- 🔗 **HDMI Audio Adapter V2a:** [Kicad_Audio_Adapter/v2a/bom/ibom.html](Kicad_Audio_Adapter/v2a/bom/ibom.html)
- 🔗 **Analog Board V3a:** [Kicad_Analog_6bit/V3a/bom/ibom.html](Kicad_Analog_6bit/V3a/bom/ibom.html)

---

## 📊 Detailed Bills of Materials (BOM)

### BOM: [CPLD Hat V6a](Kicad_6Bit/v6a)

| Ref Des | Value | Quantity | Package |
| :--- | :--- | :---: | :--- |
| **— Semiconductors —** | | | |
| U1 | XC9572XL-VQFP44 | 1 | LQFP-44, 10 x 10 mm, 0.8 mm pitch |
| D1, D2 | LED 3mm | 2 | 3 mm through-hole LED |
| **— Resistors —** | | | |
| R1, R2, R3, R4, R5, R6 | 1K | 6 | 0603 (1608 metric), SMD |
| RN1, RN2, RN3, RN4 | 4K7 | 4 | 4 x 0603 resistor array (Convex) |
| RN5, RN6, RN7, RN8 | 22R | 4 | 4 x 0603 resistor array (Convex) |
| **— Capacitors —** | | | |
| C1 | 10uF | 1 | 0805 (2012 metric), SMD |
| C2, C3, C4 | 100nF | 3 | 0805 (2012 metric), SMD |
| **— Switches —** | | | |
| SW1, SW2, SW3, SW4 | Alps Alpine SKHHBVA010 | 4 | 6 mm tactile pushbutton, THT |
| **— Sockets / Connectors —** | | | |
| P1 | Wurth Elektronik 61304021821 | 1 | 2 x 20, 2.54 mm socket, vertical |
| P2 | Samtec TSW-106-08-L-D-RA | 1 | 2 x 6, 2.54 mm pin header, right-angle |
| P4 | Wurth Elektronik 61300211821 | 1 | 1 x 2, 2.54 mm socket, vertical |
| P5 | Samtec SLW-105-01-T-D | 1 | 2 x 5, 2.54 mm socket, vertical |

---

### BOM: [HDMI Audio Adapter V2a](Kicad_Audio_Adapter/v2a)

| Ref Des | Value | Quantity | Package |
| :--- | :--- | :---: | :--- |
| **— Semiconductors —** | | | |
| U1 | PCM1808PWR | 1 | TSSOP-14, 4.4 x 5 mm, 0.65 mm pitch |
| U2 | 74LVC1G157 | 1 | SOT-363 (SC-70-6) |
| U3, U4, U5 | 74LVC1G80 | 3 | SOT-353 (SC-70-5) |
| **— Resistors —** | | | |
| R1, R2 | 470R | 2 | 0603 (1608 metric), SMD |
| R3, R5, R6 | 560R | 3 | 0603 (1608 metric), SMD |
| R4, R7 | 4K7 | 2 | 0603 (1608 metric), SMD |
| **— Capacitors —** | | | |
| C1, C2 | 1uF | 2 | 0603 (1608 metric), SMD |
| C3, C4, C12 | 10uF | 3 | 0603 (1608 metric), SMD |
| C6, C7 | 10nF | 2 | 0603 (1608 metric), SMD |
| C5, C8, C9, C10, C11 | 0.1uF | 5 | 0603 (1608 metric), SMD |
| **— Oscillator —** | | | |
| Y1 | 12.288 MHz | 1 | SMD oscillator, 4-pad, 3.2 x 2.5 mm |

---

### BOM: [Analog Board V3a](Kicad_Analog_6bit/V3a)

| Ref Des | Value | Quantity | Package |
| :--- | :--- | :---: | :--- |
| **— Semiconductors —** | | | |
| D1 | MBR130LSFT1G | 1 | SOD-123 |
| U1, U2, U3, U4, U5 | TC75W57FU | 5 | SSOP-8, 2.95 x 2.8 mm, 0.65 mm pitch |
| U6 | TS5A3159ADBVR | 1 | SOT-23-6 |
| U7 | 74LVC4066 | 1 | SOIC-14, 3.9 x 8.7 mm, 1.27 mm pitch |
| U8 | MAX5259EEE+ | 1 | QSOP-16, 3.9 x 4.9 mm, 0.635 mm pitch |
| U9 | MCP1754S-3302xCB | 1 | SOT-23 |
| **— Resistors —** | | | |
| R1 | 470R | 1 | 0805 (2012 metric), SMD |
| R2, R3, R4 | 1K | 3 | 0805 (2012 metric), SMD |
| R5 | 10K | 1 | 0805 (2012 metric), SMD |
| R6, R7, R8 | 47K | 3 | 0805 (2012 metric), SMD |
| R9, R10, R11 | 75R | 3 | 0805 (2012 metric), SMD |
| **— Capacitors —** | | | |
| C1, C2, C3, C4, C5 | 100nF | 5 | 0805 (2012 metric), SMD |
| C6, C7, C8, C9 | 10uF | 4 | 0805 (2012 metric), SMD |
| **— Sockets / Connectors —** | | | |
| P1 | Samtec SSW-106-02-T-D-RA | 1 | 2 x 6, 2.54 mm socket, right-angle |
| P2 | Samtec TLW-104-06-T-S | 1 | 1 x 4, 2.54 mm pin header, vertical |
| P4 | IDC 6pin | 1 | 3-pin, 2.54 mm, horizontal, custom footprint |
| P6, P7 | Samtec TLW-101-06-T-S | 2 | 1 x 1, 2.54 mm pin header, vertical |

---

## 📜 License & Acknowledgments

- This project is distributed under the **GNU General Public License v3.0 (GPL-3.0)**. See the [LICENSE](LICENSE) file for details.
- Original RGBtoHDMI design by David Banks ([hoglet67](https://github.com/hoglet67/RGBtoHDMI)).
- Extended development and maintenance by [IanSB](https://github.com/IanSB/RGBtoHDMI).
- Audio reverse-engineering inspiration and insights from [drdpj/RGBtoHDMI-Open-Audio](https://github.com/drdpj/RGBtoHDMI-Open-Audio).
