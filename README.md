# EMG Prosthetic Hand

Two-channel myoelectric prosthetic hand with proportional control on STM32.
Flexor digitorum superficialis closes the hand, extensor digitorum opens it.
Servo position scales proportionally with muscle activation amplitude.

## Hardware
- STM32F411 Nucleo board
- 2x INA333 instrumentation amplifiers (one per channel)
- 2x independent analog front ends
- Single servo, tendon-driven finger mechanism
- 3 surface electrodes: flexor site, extensor site, shared ground at elbow

## Signal chain (per channel)
- Input: surface EMG ~1 mV from forearm muscle
- Stage 1: INA333 instrumentation amp — differential input, high CMRR
- Stage 2: HPF at ~20 Hz — removes DC offset and baseline wander
- Stage 3: Notch filter at 60 Hz — removes power line interference
- Stage 4: LPF at ~500 Hz — removes high frequency noise
- Stage 5: Full-wave rectifier — converts bipolar EMG to unipolar
- Stage 6: Envelope detector — extracts activation amplitude
- Stage 7: Final gain stage — scales to STM32 ADC range (0–3.3 V)

## Firmware
- Dual-channel ADC sampling at 1 kSps per channel
- Max voluntary contraction calibration routine on startup
- Proportional control: servo position = f(flexor amplitude)
- Co-contraction handling: dominant channel wins, hold position on tie
- UART debug output for signal monitoring during development

## Mechanical design
- Two-finger pinch grip
- Tendon-driven actuation, spring return for opening
- Designed in SolidWorks, 3D printed

## Repo structure
firmware/     STM32 C code
kicad/        Schematic and PCB files (two-channel analog front end)
solidworks/   Mechanical design files
docs/         Datasheets and reference papers
DEVLOG.md     Weekly progress log

## Status
Week 1 — Research & planning ✅ complete
Week 2 — Design & parts order ⬜ upcoming

## References
- Geethanjali P. Myoelectric control of prosthetic hands: state-of-the-art 
  review. Med Devices (Auckl). 2016;9:247–255.
  https://pmc.ncbi.nlm.nih.gov/articles/PMC4968852/
- Ottobock bebionic hand: https://www.ottobock.com/en-us/product/8E72-61083
