# EMG Prosthetic Hand

Myoelectric prosthetic hand with EMG-based proportional control on STM32.
Two-finger pinch grip driven by forearm muscle activation (flexor digitorum superficialis).

## Hardware
- STM32F411 Nucleo board
- Instrumentation amplifier for EMG signal acquisition
- Custom analog front end: InAmp → HPF → Rectifier → Envelope detector
- Single servo, tendon-driven finger mechanism

## Signal chain
- Input: surface EMG from forearm (~1 mV)
- Envelope detection for proportional control output
- ADC input: 0–3.3 V, 12-bit

## Mechanical design
- Two-finger pinch grip
- Tendon-driven actuation
- Designed in SolidWorks, 3D printed

## Repo structure
firmware/     STM32 C code
kicad/        Schematic and PCB files
solidworks/   Mechanical design files
docs/         Datasheets and reference papers
DEVLOG.md     Weekly progress log

## Status
Week 1 — Research & planning in progress
