# 3bit-dac-ltspice
3-bit DAC designed in LTspice using an asynchronous ripple counter, binary-weighted resistor network, and op-amp summing. Produces a clean 8-level analog staircase output.

# 3-Bit Digital-to-Analog Converter — LTspice

## Project Overview

A complete 3-bit Digital-to-Analog Converter (DAC) designed and simulated in LTspice. The circuit converts a 3-bit binary count into a corresponding analog voltage using a binary-weighted resistor network and op-amp summing amplifier.

## Architecture

The DAC consists of three main stages:

| Stage | Components | Role |
| :--- | :--- | :--- |
| **Counter** | 3 D flip-flops (A1, A2, A3) | Generates a 3-bit binary count from a clock signal |
| **Buffers** | 3 digital buffers (A4, A5, A6) | Scale logic levels to 5V (Vhigh=5, Vlow=0) |
| **Summing Network** | Binary-weighted resistors (40k, 20k, 10k) + 2 LT1001 op-amps | Converts binary-weighted currents to analog voltage |

## Circuit Details

- **3 D flip-flops** cascaded as an asynchronous binary ripple counter
- **3 digital buffers** with Vhigh=5V, Vlow=0
- **Binary-weighted resistors**: 40kΩ (MSB), 20kΩ, 10kΩ (LSB)
- **Two LT1001 op-amps**: U1 for summing, U2 for buffering
- **Dual ±15V supply rails** (V2, V3)

## Simulation Setup

- **Clock**: `PULSE(0 5 0 1n 1n 0.5m 1m)`
- **Simulation**: `.tran 0 15m 0 40u`

## Results

The output produces a clean 8-level analog staircase:

- **0V** at binary 000
- **~0.2V** at binary 001
- **~0.4V** at binary 010
- **~0.6V** at binary 011
- **~0.8V** at binary 100
- **~1.0V** at binary 101
- **~1.2V** at binary 110
- **~1.4V** at binary 111

The staircase increments smoothly and resets exactly at the **8ms** mark, matching 2³ = 8 binary states.

## Files Included

- `dac_3bit.asc` — LTspice schematic file
- `schematic.png` — Full schematic view
- `waveforms.png` — Staircase output waveform (cursor at 0.72ms)
- `waveforms_second.png` — Waveform with cursor at 4.56ms showing mid-cycle transition

## Tools Used

- **LTspice** (Analog Devices) — SPICE simulator
- **LT1001 op-amp models**

## What I Learned

- Digital-to-analog conversion using binary-weighted resistor networks
- Ripple counter design with cascaded D flip-flops
- Op-amp summing amplifier configuration
- Mixed-signal circuit simulation in LTspice
- Debugging clock timing issues in digital circuits

## Author

Ninad Shende
MSc Electronics and Electrical Engineering, University of Glasgow
