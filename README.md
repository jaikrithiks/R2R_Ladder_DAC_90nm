# 4-Bit R-2R DAC Design Using Cadence Virtuoso (90nm)

## Overview

This project presents the design, simulation, layout implementation, and verification of a 4-bit R-2R Digital-to-Analog Converter (DAC) using Cadence Virtuoso.

The design is implemented using the **gpdk090 (90nm CMOS) technology** and follows a full-custom VLSI design methodology. The project focuses on understanding the operation of an R-2R resistor ladder, generating analog output levels from digital inputs, and validating the design through physical implementation and post-layout simulation.

The project also includes the design and analysis of supporting analog circuits, including a common-source amplifier, differential amplifier, and operational amplifier.

## Project Specifications

| Parameter | Value |
|---|---|
| Project | 4-Bit R-2R DAC |
| EDA Tool | Cadence Virtuoso |
| Technology Node | 90nm (gpdk090) |
| DAC Resolution | 4-bit |
| Supply Voltage (VDD) | +2.5 V |
| Negative Supply (VSS) | -2.5 V |
| Digital Logic Levels | 0 V and 1.8 V |
| Unit Resistance (R) | 1 kΩ |
| Ladder Resistance (2R) | 2 kΩ |
| Resistor Model | ressnpoly_2 |
| DC Current | 30 µA |

## R-2R DAC Architecture

The R-2R DAC uses a repeating network of resistors with values R and 2R to generate an analog output corresponding to a 4-bit digital input.

Each input bit contributes a binary-weighted fraction of the reference voltage. The most significant bit (D3) contributes the largest fraction, while the least significant bit (D0) contributes the smallest.

The ideal normalized output relationship is:

\[
V_{OUT}=V_{REF}\left(\frac{D_3}{2}+
\frac{D_2}{4}+\frac{D_1}{8}+\frac{D_0}{16}\right)
\]

This architecture provides a relatively simple implementation using only two resistor values.

## Design Implementation

The project follows the complete schematic-to-layout design flow in Cadence Virtuoso.

### 1. Analog Building Blocks

The following analog circuits were designed and analyzed as part of the project:

- Common-Source Amplifier
- Differential Amplifier
- Operational Amplifier

Their implementation includes schematic design, testbench development, circuit analysis, and layout work.

### 2. R-2R DAC Schematic Design

- Designed a 4-bit R-2R resistor ladder.
- Implemented the circuit using 1 kΩ and 2 kΩ resistor values.
- Configured digital input branches to represent the four input bits.
- Established the required supply and reference voltage conditions.

### 3. Testbench Development

A dedicated testbench was developed to evaluate all 16 possible digital input combinations.

Four periodic pulse sources were used to generate the digital inputs. Their pulse widths and periods were selected according to the binary significance of each bit.

| Input | Pulse Width | Period |
|---|---:|---:|
| D0 | 5 µs | 10 µs |
| D1 | 10 µs | 20 µs |
| D2 | 20 µs | 40 µs |
| D3 | 40 µs | 80 µs |

Transient analysis was performed to observe the digital input patterns and corresponding analog output levels.

### 4. Functional Verification

The DAC output was measured for all 16 input combinations.

The simulated output increases with the digital input code, demonstrating the expected staircase-like DAC transfer characteristic.

| Decimal | Digital Input | Output Voltage |
|---:|:---:|---:|
| 0 | 0000 | -1.89 mV |
| 1 | 0001 | 111 mV |
| 2 | 0010 | 223 mV |
| 3 | 0011 | 336 mV |
| 4 | 0100 | 448 mV |
| 5 | 0101 | 561 mV |
| 6 | 0110 | 673 mV |
| 7 | 0111 | 786 mV |
| 8 | 1000 | 898 mV |
| 9 | 1001 | 1.01 V |
| 10 | 1010 | 1.12 V |
| 11 | 1011 | 1.24 V |
| 12 | 1100 | 1.35 V |
| 13 | 1101 | 1.46 V |
| 14 | 1110 | 1.57 V |
| 15 | 1111 | 1.69 V |

**Measured output range:** Approximately -1.89 mV to 1.69 V.

**Average step size:** Approximately 113 mV, calculated using the measured endpoints.

### 5. Layout and Physical Verification

The R-2R DAC schematic was translated into a full-custom physical layout using Cadence Virtuoso.

The physical design and verification process included:

- Full-custom layout implementation.
- Design Rule Check (DRC).
- Layout Versus Schematic (LVS).
- Parasitic resistance and capacitance extraction.

### 6. Post-Layout Simulation

After physical verification, the layout was used to generate an extracted circuit representation containing parasitic resistance and capacitance.

Post-layout simulation was performed to evaluate the circuit response with physical parasitic effects.

The pre-layout and post-layout waveforms were examined to assess the effect of layout parasitics on the DAC output.

## Design Flow

1. Circuit architecture and specification definition.
2. R-2R ladder schematic implementation.
3. Testbench development.
4. Transient simulation and functional verification.
5. DAC output measurement for all 16 input codes.
6. Full-custom layout implementation.
7. DRC and LVS verification.
8. Parasitic RC extraction.
9. Post-layout simulation.
10. GDS generation.

## Tools and Technologies

- **Cadence Virtuoso:** Schematic design, simulation, layout, and physical verification.
- **gpdk090:** 90nm CMOS process design kit.
- **Spectre:** Circuit simulation environment.
- **DRC/LVS:** Physical design verification.
- **RC Extraction:** Parasitic extraction and post-layout analysis.

## Repository Contents

The repository is organized to include the following project materials:

- `schematic/` – Circuit schematics.
- `testbench/` – Simulation testbench configurations.
- `simulation/` – Transient analysis and simulation results.
- `layout/` – Full-custom layout screenshots and design files.
- `verification/` – DRC and LVS verification results.
- `post-layout/` – Extracted views and post-layout simulation results.
- `report/` – Detailed project report.
- `gds/` – Generated GDS layout file.

*The directory names above describe the suggested repository organization; adjust them to match the actual uploaded files.*

## Conclusion

The project demonstrates the complete design flow of a 4-bit R-2R DAC using Cadence Virtuoso and a 90nm technology library.

The implementation covers circuit design, transient simulation, DAC transfer-characteristic analysis, full-custom layout, physical verification, parasitic extraction, and post-layout simulation.

The measured results demonstrate the conversion of all 16 digital input codes into corresponding analog output levels.

## Reference

Jahnavi, E., E. Chandrasekhar, and P. Chandrasekhar. "Design of 4-bit Binary Weighted DAC in 180nm CMOS Technology." *International Journal of Microsystems and IoT*, 2.8 (2023): 1112–1117.

---

**Project:** 4-Bit R-2R DAC  
**Technology:** 90nm CMOS (gpdk090)  
**EDA Platform:** Cadence Virtuoso  
**Course:** Introduction to VLSI  

