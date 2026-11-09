# RGBtoHDMI

RGBtoHDMI converts compatible video from vintage computers to HDMI using
a Raspberry Pi Zero, custom firmware, and a CPLD. This repository contains
three board designs:

- **CPLD Hat V6a:** a 12-bit digital RGB interface for the Raspberry Pi.
- **Analog board V3a:** an add-on for sources with a limited number of analog
  RGB/YUV levels or monochrome composite video; it is not intended for
  full-range analog RGB.
- **HDMI Audio Adapter V2a:** an optional, reverse-engineered replica of the
  RGBtoHDMI audio add-on for the CPLD Hat. See the related
  [RGBtoHDMI Open Audio project](https://github.com/drdpj/RGBtoHDMI-Open-Audio).

## Bill of Materials

The tables list each component's reference designator, value, quantity, and
package. References with the same value and package are grouped together.
Interactive BOMs: [CPLD Hat V6a](Kicad_6Bit/v6a/bom/ibom.html) and
[HDMI Audio Adapter V2a](Kicad_Audio_Adapter/v2a/bom/ibom.html).
The Analog V3a BOM below is based on local design files; those files are not
currently tracked in GitHub. For sourcing information on upstream boards, see
the project's [12-bit board BOM](https://github.com/IanSB/RGBtoHDMI/wiki/Bill-of-Materials-%2812-Bit-Board)
and [HDMI Audio documentation](https://github.com/IanSB/RGBtoHDMI/wiki/Audio).

## Board variants and differences

- **CPLD Hat V6a and upstream V4:** both are 12-bit designs. Compared with the
  upstream [Issue 4 (V4) board](https://github.com/IanSB/RGBtoHDMI/tree/master/Kicad_6Bit/v4),
  V6a uses SMD resistor arrays instead of through-hole arrays.
- **CPLD Hat V6a and upstream V6:** V6a uses through-hole pushbuttons instead
  of V6's SMD buttons, whose small pads can be damaged during replacement.
  Otherwise, V6a is an exact copy of V6. The upstream V6 files are not in the
  [upstream GitHub repository](https://github.com/IanSB/RGBtoHDMI).
- **Analog V3a:** compared with the upstream
  [V3 analog board](https://github.com/IanSB/RGBtoHDMI/tree/master/kicad_analog_6bit/V3),
  the only change is replacing the MAX9144 comparators with lower-cost
  TC75W57FU comparators.

## BOM: [CPLD Hat V6a](Kicad_6Bit/v6a)

### Semiconductors

| Ref Des | Value           | Quantity | Package                                  |
| ------- | --------------- | -------- | ---------------------------------------- |
| U1      | XC9572XL-VQFP44 | 1        | LQFP-44, 10 x 10 mm, 0.8 mm pitch        |
| D1, D2  | LED 3mm         | 2        | 3 mm through-hole LED                    |

### Resistors

| Ref Des                   | Value | Quantity | Package                          |
| ------------------------- | ----- | -------- | -------------------------------- |
| R1, R2, R3, R4, R5, R6    | 1K    | 6        | 0603 (1608 metric), SMD          |
| RN1, RN2, RN3, RN4        | 4K7   | 4        | 4 x 0603 resistor array (Convex) |
| RN5, RN6, RN7, RN8        | 22R   | 4        | 4 x 0603 resistor array (Convex) |

### Capacitors

| Ref Des    | Value | Quantity | Package                    |
| ---------- | ----- | -------- | -------------------------- |
| C1         | 10uF  | 1        | 0805 (2012 metric), SMD    |
| C2, C3, C4 | 100nF | 3        | 0805 (2012 metric), SMD    |

### Switches

| Ref Des            | Value                  | Quantity | Package                         |
| ------------------ | ---------------------- | -------- | ------------------------------- |
| SW1, SW2, SW3, SW4 | Alps Alpine SKHHBVA010 | 4        | 6 mm tactile pushbutton, THT    |

### Sockets / Connectors

| Ref Des | Value                        | Quantity | Package                                   |
| ------- | ---------------------------- | -------- | ----------------------------------------- |
| P1      | Wurth Elektronik 61304021821 | 1        | 2 x 20, 2.54 mm socket, vertical          |
| P2      | Samtec TSW-106-08-L-D-RA     | 1        | 2 x 6, 2.54 mm pin header, right-angle    |
| P4      | Wurth Elektronik 61300211821 | 1        | 1 x 2, 2.54 mm socket, vertical           |
| P5      | Samtec SLW-105-01-T-D        | 1        | 2 x 5, 2.54 mm socket, vertical           |

## BOM: [Analog Board V3a](Kicad_Analog_6bit/V3a)

### Semiconductors

| Ref Des            | Value             | Quantity | Package                               |
| ------------------ | ----------------- | -------- | ------------------------------------- |
| D1                 | MBR130LSFT1G      | 1        | SOD-123                               |
| U1, U2, U3, U4, U5 | TC75W57FU         | 5        | SSOP-8, 2.95 x 2.8 mm, 0.65 mm pitch  |
| U6                 | TS5A3159ADBVR     | 1        | SOT-23-6                              |
| U7                 | 74LVC4066         | 1        | SOIC-14, 3.9 x 8.7 mm, 1.27 mm pitch  |
| U8                 | MAX5259EEE+       | 1        | QSOP-16, 3.9 x 4.9 mm, 0.635 mm pitch |
| U9                 | MCP1754S-3302xCB  | 1        | SOT-23                                |

### Resistors

| Ref Des       | Value | Quantity | Package                 |
| ------------- | ----- | -------- | ----------------------- |
| R1            | 470R  | 1        | 0805 (2012 metric), SMD |
| R2, R3, R4    | 1K    | 3        | 0805 (2012 metric), SMD |
| R5            | 10K   | 1        | 0805 (2012 metric), SMD |
| R6, R7, R8    | 47K   | 3        | 0805 (2012 metric), SMD |
| R9, R10, R11  | 75R   | 3        | 0805 (2012 metric), SMD |

### Capacitors

| Ref Des             | Value | Quantity | Package                 |
| ------------------- | ----- | -------- | ----------------------- |
| C1, C2, C3, C4, C5  | 100nF | 5        | 0805 (2012 metric), SMD |
| C6, C7, C8, C9      | 10uF  | 4        | 0805 (2012 metric), SMD |

### Sockets / Connectors

| Ref Des | Value                       | Quantity | Package                                       |
| ------- | --------------------------- | -------- | --------------------------------------------- |
| P6, P7  | Samtec TLW-101-06-T-S       | 2        | 1 x 1, 2.54 mm pin header, vertical           |
| P1      | Samtec SSW-106-02-T-D-RA    | 1        | 2 x 6, 2.54 mm socket, right-angle            |
| P2      | Samtec TLW-104-06-T-S       | 1        | 1 x 4, 2.54 mm pin header, vertical           |
| P4      | IDC 6pin                    | 1        | 3-pin, 2.54 mm, horizontal, custom footprint |

## BOM: [HDMI Audio Adapter V2a](Kicad_Audio_Adapter/v2a)

### Semiconductors

| Ref Des    | Value      | Quantity | Package                             |
| ---------- | ---------- | -------- | ----------------------------------- |
| U1         | PCM1808PWR | 1        | TSSOP-14, 4.4 x 5 mm, 0.65 mm pitch |
| U2         | 74LVC1G157 | 1        | SOT-363 (SC-70-6)                   |
| U3, U4, U5 | 74LVC1G80  | 3        | SOT-353 (SC-70-5)                   |

### Resistors

| Ref Des     | Value | Quantity | Package                 |
| ----------- | ----- | -------- | ----------------------- |
| R1, R2      | 470R  | 2        | 0603 (1608 metric), SMD |
| R3, R5, R6  | 560R  | 3        | 0603 (1608 metric), SMD |
| R4, R7      | 4K7   | 2        | 0603 (1608 metric), SMD |

### Capacitors

| Ref Des              | Value | Quantity | Package                 |
| -------------------- | ----- | -------- | ----------------------- |
| C1, C2               | 1uF   | 2        | 0603 (1608 metric), SMD |
| C3, C4, C12          | 10uF  | 3        | 0603 (1608 metric), SMD |
| C6, C7               | 10nF  | 2        | 0603 (1608 metric), SMD |
| C5, C8, C9, C10, C11 | 0.1uF | 5        | 0603 (1608 metric), SMD |

### Oscillator

| Ref Des | Value      | Quantity | Package                             |
| ------- | ---------- | -------- | ----------------------------------- |
| Y1      | 12.288 MHz | 1        | SMD oscillator, 4-pad, 3.2 x 2.5 mm |
