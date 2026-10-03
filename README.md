# 2-to-1 CMOS Transmission-Gate Multiplexer

An LTspice implementation and transient-simulation study of a 2-to-1 multiplexer built with CMOS transmission gates. This project is a learning exercise in CMOS switch-level design, complementary control signals, and verifying digital selection behavior in an EDA simulation environment.

## Overview

A 2-to-1 multiplexer selects one of two data inputs and connects it to a single output. In this circuit, CMOS transmission gates act as bidirectional switches:

- When `S = 0`, the transmission gate on `D0` is enabled, so `Y` follows `D0`.
- When `S = 1`, the transmission gate on `D1` is enabled, so `Y` follows `D1`.

The selection function is:

```text
Y = S̅·D0 + S·D1
```

## CMOS Transmission-Gate Control

Each transmission gate uses an NMOS and a PMOS in parallel. Their complementary gate controls allow both logic-low and logic-high signals to pass effectively.

| Selected path | NMOS control | PMOS control | Result |
|---|---:|---:|---|
| `D0 → Y` | `S̅` | `S` | Enabled when `S = 0` |
| `D1 → Y` | `S` | `S̅` | Enabled when `S = 1` |

An inverter generates `S̅` from the select input `S`, ensuring that only one data path is enabled at a time.

## Simulation

The LTspice schematic uses 5 V logic levels and a transient analysis to exercise the two data inputs and the select signal. The resulting waveform verifies that the output changes with the selected input:

- With `S` low, `Y` tracks `D0`.
- With `S` high, `Y` tracks `D1`.

## Project Files

```text
.
├── 2to1_TG_Mux.asc   # LTspice schematic and simulation setup
├── MUX_CIRCUIT.pdf   # Exported circuit schematic
├── MUX_WAVE.pdf      # Transient-simulation waveform
└── README.md         # Project documentation
```

## View the Design and Results

- [Circuit schematic (PDF)](MUX_CIRCUIT.pdf)
- [Simulation waveform (PDF)](MUX_WAVE.pdf)

## How to Run

1. Open `2to1_TG_Mux.asc` in LTspice.
2. Run the configured transient simulation.
3. Plot the data inputs, select signals, and output to confirm the multiplexer operation.

## Learning Outcomes

- Design a basic 2-to-1 multiplexer at the transistor/switch level.
- Use CMOS transmission gates to pass both logic levels.
- Generate and apply complementary select signals (`S` and `S̅`).
- Verify digital behavior through LTspice transient waveforms.

## Tools

- LTspice

---

*Created as part of a VLSI/EDA learning portfolio.*
