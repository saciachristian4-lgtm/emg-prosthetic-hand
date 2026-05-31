# Dev log

## 2026-05-31

- Created repo and set up documentation
- Decided on two-channel proportional myoelectric control scope
- Channel 1: flexor digitorum superficialis → proportional close
- Channel 2: extensor digitorum → proportional open
- Mechanical: spring return for finger opening, single servo for close
- Key challenge identified: co-contraction handling in firmware
- Key challenge identified: two independent noise environments on PCB

**Read:** Geethanjali 2016 — Myoelectric control of prosthetic hands: 
state-of-the-art review (PMC4968852)

**Learned:**
- Proportional control maps EMG envelope linearly to motor voltage — 
  chosen over on/off (no natural feel) and pattern recognition 
  (training overhead, degrades in real use, overkill for one DOF)
- FSM adds value only with 4+ grip patterns — not justified for 
  this scope
- Flexor digitorum superficialis confirmed as correct electrode site — 
  superficial, large, consistent signal in literature
- Surface EMG standard for non-invasive prosthesis control — 
  3–4 usable sites on residual limb

**Decisions locked:**
- Control strategy: 2-channel proportional
- Muscle sites: flexor digitorum superficialis (close), 
  extensor digitorum (open)
- Opening mechanism: spring return

**Next:** Order parts Week 2, complete SolidWorks finger geometry sketch
