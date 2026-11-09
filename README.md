<!-- markdownlint-disable-file MD033 -->
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
- **Through-Hole Tactile Switches:** Uses standard, readily available 6 mm through-hole tactile pushbuttons (**Alps Alpine SKHHBVA010**) instead of SMD buttons. This change was directly motivated by real-world repair experience: when the buttons on a commercial V6 board failed, several delicate surface-mount pads tore off during desoldering, and finding identical replacement SMD switches proved difficult. THT switches make soldering, future replacements, and long-term maintenance significantly easier and more robust.
- **Quick Links:** [Schematic (PDF)](Kicad_6Bit/v6a/rgb-to-hdmi.pdf) · [Interactive BOM](Kicad_6Bit/v6a/bom/ibom.html) · [Fabrication Files](Kicad_6Bit/v6a/manufacturing/)

### 2. HDMI Audio Adapter V2a (Audio Add-on Replica)

- **100% Open Hardware Clean-Room Reverse Engineering:** The audio add-on was previously only distributed as closed commercial hardware without public schematics or Gerber files. This replica brings the hardware back into the open-source community. See also the related [RGBtoHDMI Open Audio project](https://github.com/drdpj/RGBtoHDMI-Open-Audio).
- **Plug-and-Play:** Stacks directly onto header `P2` of the CPLD Hat to feed digital I2S audio into the Raspberry Pi Zero for embedding into the HDMI stream.
- **Quick Links:** [Schematic (PDF)](Kicad_Audio_Adapter/v2a/rgbtohdmi-audio.pdf) · [Interactive BOM](Kicad_Audio_Adapter/v2a/bom/ibom.html) · [Fabrication Files](Kicad_Audio_Adapter/v2a/manufacturing/)

### 3. Analog Board V3a (Analog RGB/YUV Add-on)

- **Cost-Optimized Design:** Compared with the upstream [V3 analog board](https://github.com/IanSB/RGBtoHDMI/tree/master/kicad_analog_6bit/V3), this revision replaces the expensive and hard-to-source `MAX9144` quad comparators with accessible, cost-effective `TC75W57FU` dual comparators.
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
| **PCB Thickness** | **1.6 mm** for CPLD Hat V6a & Analog Board V3a<br>**0.8 mm** for HDMI Audio Adapter V2a |
| **Copper Weight** | 1 oz (35 µm) |
| **Surface Finish** | **ENIG** (recommended for fine-pitch packages: PCM1808 TSSOP-14, XC9572XL VQFP-44) or **Lead-Free HASL** |
| **Solder Mask** | Green (or preferred color) |
| **Silkscreen** | White |

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

<table width="100%">
  <thead>
    <tr>
      <th width="25%" align="left">Ref Des</th>
      <th width="25%" align="left">Value</th>
      <th width="10%" align="center">Quantity</th>
      <th width="40%" align="left">Package</th>
    </tr>
  </thead>
  <tbody>
    <tr><th colspan="4" align="left">Semiconductors</th></tr>
    <tr><td>U1</td><td>XC9572XL-VQFP44</td><td align="center">1</td><td>LQFP-44, 10 x 10 mm, 0.8 mm pitch</td></tr>
    <tr><td>D1, D2</td><td>LED 3mm</td><td align="center">2</td><td>3 mm through-hole LED</td></tr>
    <tr><th colspan="4" align="left">Resistors</th></tr>
    <tr><td>R1, R2, R3, R4, R5, R6</td><td>1K</td><td align="center">6</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><td>RN1, RN2, RN3, RN4</td><td>4K7</td><td align="center">4</td><td>4 x 0603 resistor array (Convex)</td></tr>
    <tr><td>RN5, RN6, RN7, RN8</td><td>22R</td><td align="center">4</td><td>4 x 0603 resistor array (Convex)</td></tr>
    <tr><th colspan="4" align="left">Capacitors</th></tr>
    <tr><td>C1</td><td>10uF</td><td align="center">1</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><td>C2, C3, C4</td><td>100nF</td><td align="center">3</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><th colspan="4" align="left">Switches</th></tr>
    <tr><td>SW1, SW2, SW3, SW4</td><td>Alps Alpine SKHHBVA010</td><td align="center">4</td><td>6 mm tactile pushbutton, THT</td></tr>
    <tr><th colspan="4" align="left">Sockets / Connectors</th></tr>
    <tr><td>P1</td><td>Wurth Elektronik 61304021821</td><td align="center">1</td><td>2 x 20, 2.54 mm socket, vertical</td></tr>
    <tr><td>P2</td><td>Samtec TSW-106-08-L-D-RA</td><td align="center">1</td><td>2 x 6, 2.54 mm pin header, right-angle</td></tr>
    <tr><td>P4</td><td>Wurth Elektronik 61300211821</td><td align="center">1</td><td>1 x 2, 2.54 mm socket, vertical</td></tr>
    <tr><td>P5</td><td>Samtec SLW-105-01-T-D</td><td align="center">1</td><td>2 x 5, 2.54 mm socket, vertical</td></tr>
  </tbody>
</table>

---

### BOM: [HDMI Audio Adapter V2a](Kicad_Audio_Adapter/v2a)

<table width="100%">
  <thead>
    <tr>
      <th width="25%" align="left">Ref Des</th>
      <th width="25%" align="left">Value</th>
      <th width="10%" align="center">Quantity</th>
      <th width="40%" align="left">Package</th>
    </tr>
  </thead>
  <tbody>
    <tr><th colspan="4" align="left">Semiconductors</th></tr>
    <tr><td>U1</td><td>PCM1808PWR</td><td align="center">1</td><td>TSSOP-14, 4.4 x 5 mm, 0.65 mm pitch</td></tr>
    <tr><td>U2</td><td>74LVC1G157</td><td align="center">1</td><td>SOT-363 (SC-70-6)</td></tr>
    <tr><td>U3, U4, U5</td><td>74LVC1G80</td><td align="center">3</td><td>SOT-353 (SC-70-5)</td></tr>
    <tr><th colspan="4" align="left">Resistors</th></tr>
    <tr><td>R1, R2</td><td>470R</td><td align="center">2</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><td>R3, R5, R6</td><td>560R</td><td align="center">3</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><td>R4, R7</td><td>4K7</td><td align="center">2</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><th colspan="4" align="left">Capacitors</th></tr>
    <tr><td>C1, C2</td><td>1uF</td><td align="center">2</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><td>C3, C4, C12</td><td>10uF</td><td align="center">3</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><td>C6, C7</td><td>10nF</td><td align="center">2</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><td>C5, C8, C9, C10, C11</td><td>0.1uF</td><td align="center">5</td><td>0603 (1608 metric), SMD</td></tr>
    <tr><th colspan="4" align="left">Oscillator</th></tr>
    <tr><td>Y1</td><td>12.288 MHz</td><td align="center">1</td><td>SMD oscillator, 4-pad, 3.2 x 2.5 mm</td></tr>
  </tbody>
</table>

---

### BOM: [Analog Board V3a](Kicad_Analog_6bit/V3a)

<table width="100%">
  <thead>
    <tr>
      <th width="25%" align="left">Ref Des</th>
      <th width="25%" align="left">Value</th>
      <th width="10%" align="center">Quantity</th>
      <th width="40%" align="left">Package</th>
    </tr>
  </thead>
  <tbody>
    <tr><th colspan="4" align="left">Semiconductors</th></tr>
    <tr><td>D1</td><td>MBR130LSFT1G</td><td align="center">1</td><td>SOD-123</td></tr>
    <tr><td>U1, U2, U3, U4, U5</td><td>TC75W57FU</td><td align="center">5</td><td>SSOP-8, 2.95 x 2.8 mm, 0.65 mm pitch</td></tr>
    <tr><td>U6</td><td>TS5A3159ADBVR</td><td align="center">1</td><td>SOT-23-6</td></tr>
    <tr><td>U7</td><td>74LVC4066</td><td align="center">1</td><td>SOIC-14, 3.9 x 8.7 mm, 1.27 mm pitch</td></tr>
    <tr><td>U8</td><td>MAX5259EEE+</td><td align="center">1</td><td>QSOP-16, 3.9 x 4.9 mm, 0.635 mm pitch</td></tr>
    <tr><td>U9</td><td>MCP1754S-3302xCB</td><td align="center">1</td><td>SOT-23</td></tr>
    <tr><th colspan="4" align="left">Resistors</th></tr>
    <tr><td>R1</td><td>470R</td><td align="center">1</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><td>R2, R3, R4</td><td>1K</td><td align="center">3</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><td>R5</td><td>10K</td><td align="center">1</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><td>R6, R7, R8</td><td>47K</td><td align="center">3</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><td>R9, R10, R11</td><td>75R</td><td align="center">3</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><th colspan="4" align="left">Capacitors</th></tr>
    <tr><td>C1, C2, C3, C4, C5</td><td>100nF</td><td align="center">5</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><td>C6, C7, C8, C9</td><td>10uF</td><td align="center">4</td><td>0805 (2012 metric), SMD</td></tr>
    <tr><th colspan="4" align="left">Sockets / Connectors</th></tr>
    <tr><td>P1</td><td>Samtec SSW-106-02-T-D-RA</td><td align="center">1</td><td>2 x 6, 2.54 mm socket, right-angle</td></tr>
    <tr><td>P2</td><td>Samtec TLW-104-06-T-S</td><td align="center">1</td><td>1 x 4, 2.54 mm pin header, vertical</td></tr>
    <tr><td>P4</td><td>IDC 6pin</td><td align="center">1</td><td>3-pin, 2.54 mm, horizontal, custom footprint</td></tr>
    <tr><td>P6, P7</td><td>Samtec TLW-101-06-T-S</td><td align="center">2</td><td>1 x 1, 2.54 mm pin header, vertical</td></tr>
  </tbody>
</table>

---

## 📜 License & Acknowledgments

- This project is distributed under the **GNU General Public License v3.0 (GPL-3.0)**. See the [LICENSE](LICENSE) file for details.
- Original RGBtoHDMI design by David Banks ([hoglet67](https://github.com/hoglet67/RGBtoHDMI)).
- Extended development and maintenance by [IanSB](https://github.com/IanSB/RGBtoHDMI).
- Audio reverse-engineering inspiration and insights from [drdpj/RGBtoHDMI-Open-Audio](https://github.com/drdpj/RGBtoHDMI-Open-Audio).
