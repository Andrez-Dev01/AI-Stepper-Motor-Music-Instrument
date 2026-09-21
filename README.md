# AI Stepper Motor Music Instrument

A hardware + software music instrument that uses stepper motors to physically generate musical sounds.

The project begins with a small hardware kit and progressively develops into a coordinated multi-motor musical system. The long-term goal is to combine real-time motor control, musical scheduling, digital audio analysis, and AI-assisted music transcription.

```text id="x2b6cc"
User Input / Audio
        ↓
Musical Representation
        ↓
Note & Timing Scheduler
        ↓
Motor Control
        ↓
Motor Drivers
        ↓
Stepper Motors
        ↓
Mechanical Sound
```

The long-term audio/AI pipeline expands this into:

```text id="q8gqyb"
Audio Input
    ↓
Audio Preprocessing
    ↓
Pitch / Note Detection
    ↓
Timing Detection
    ↓
Musical Events
    ↓
AI-Assisted Interpretation
    ↓
Note & Timing Scheduler
    ↓
Motor Control
    ↓
Physical Instrument
```

The project combines hardware, software, real-time timing, audio processing, experimentation, and AI.

---

# Project Goals

The project is designed to investigate:

- Stepper motor control
- Motor timing
- Mechanical sound generation
- Real-time scheduling
- Musical note representation
- Multi-motor synchronization
- Audio signal processing
- Pitch detection
- Timing detection
- AI-assisted music transcription
- Hardware/software integration
- Latency
- Repeatability
- Physical system constraints

The central question is:

> **Can software translate musical information into precisely timed physical motor movement that produces a controllable musical instrument?**

---

# Project Philosophy

This project will be developed incrementally.

The first version does **not** need AI.

The first objective is to understand the physical system.

```text id="c4tr8m"
Hardware
   ↓
One Motor
   ↓
Repeatable Movement
   ↓
Repeatable Sound
   ↓
Musical Notes
   ↓
Multiple Motors
   ↓
Audio Input
   ↓
AI Experiments
```

Each stage must work before the next layer is added.

This prevents the project from becoming an AI demonstration with poorly understood hardware underneath it.

---

# Initial Hardware

The first phase will identify and document the components already available.

Potential components include:

- Stepper motors
- Motor drivers
- Microcontroller
- Power supply
- Breadboard / wiring
- Connectors
- Mechanical components
- Sound-producing mechanism

The exact hardware configuration will be documented after each component is identified.

---

# Hardware Baseline

Before building the complete instrument, the project will establish:

```text id="1h3zcu"
Motor
 ↓
Driver
 ↓
Controller
 ↓
Power
```

The first experiments will determine:

- Motor type
- Driver type
- Controller capabilities
- Required voltage/current
- Wiring
- Step resolution
- Maximum usable speed
- Safe operating range
- Heat generation
- Mechanical movement
- Sound mechanism

Hardware documentation will include diagrams and photographs where appropriate.

---

# Phase 1 — Single Motor Control

The first software goal is simple:

> Make one motor move predictably.

Conceptually:

```text id="yt2kq6"
Command
   ↓
Controller
   ↓
Driver
   ↓
Stepper Motor
   ↓
Movement
```

The controller should eventually be able to specify:

```text id="y7g3x1"
Direction
Speed
Number of steps
Acceleration
Timing
```

Example conceptual command:

```text id="bd7cxq"
move(
    steps = 400,
    direction = forward,
    step_delay = X
)
```

Actual values will depend on the motor and driver.

---

# Phase 2 — Understanding the Sound

Movement alone is not enough.

The project will investigate how motor movement produces sound.

Experiments may vary:

- Step frequency
- Motor speed
- Acceleration
- Direction
- Resonance
- Mechanical contact
- Material
- Motor load
- Step resolution

The goal is to determine:

```text id="rpspmi"
Motor Movement
      ↓
Frequency / Timing
      ↓
Mechanical Vibration
      ↓
Audible Sound
```

Measurements and observations will be documented rather than assuming that a particular motor behavior will produce a desired note.

---

# Phase 3 — Musical Note Mapping

Once repeatable sound is established, the system can begin mapping motor behavior to musical information.

Conceptually:

```text id="r1n9tr"
Musical Note
     ↓
Target Frequency
     ↓
Motor Timing
     ↓
Step Frequency
     ↓
Physical Sound
```

For example, the software may eventually represent:

```text id="y9q5dn"
Note:
A4

Frequency:
440 Hz

Duration:
500 ms
```

The exact relationship between musical frequency and motor behavior will depend on the mechanical design.

This relationship will therefore be measured experimentally.

---

# Phase 4 — Musical Event Scheduler

The project will introduce a scheduling layer that represents music as timed events.

Example:

```text id="1r6u6r"
Time 0 ms:
    Motor 1 → C4

Time 500 ms:
    Motor 1 → E4

Time 1000 ms:
    Motor 1 → G4
```

A musical sequence can then be represented programmatically:

```text id="ldf9u6"
[
    {note: C4, start: 0ms, duration: 500ms},
    {note: E4, start: 500ms, duration: 500ms},
    {note: G4, start: 1000ms, duration: 500ms}
]
```

This creates a separation between:

```text id="d93b4j"
WHAT should be played?
        ↓
HOW should the motor produce it?
```

---

# Phase 5 — Software Input

The instrument will eventually support different input methods.

Potential inputs:

### Computer Keyboard

```text id="lv2dqt"
A → Note
S → Note
D → Note
F → Note
```

### Virtual Keyboard

A software interface can provide:

```text id="y7pjzj"
┌───┬───┬───┬───┬───┐
│ C │ D │ E │ F │ G │
└───┴───┴───┴───┴───┘
```

### Programmatic Music

```text id="3wqzcy"
play([
    C4,
    E4,
    G4,
    C5
])
```

### MIDI-Style Events

Eventually:

```text id="r7df2k"
NOTE_ON
NOTE_OFF
VELOCITY
TIMESTAMP
```

The input system should remain separate from the hardware-control layer.

---

# Phase 6 — Multiple Motors

The project will eventually expand from one motor to multiple motors.

```text id="l8xjkj"
                  Scheduler
                /     |     \
               ↓      ↓      ↓
           Motor 1  Motor 2  Motor 3
               ↓      ↓      ↓
             Sound  Sound  Sound
```

This introduces new engineering problems:

- Synchronization
- Timing drift
- Concurrent control
- Scheduling
- Motor-driver limitations
- Power requirements
- CPU/microcontroller limitations
- Mechanical interference
- Polyphonic sound

The system should measure whether multiple motors actually remain synchronized rather than assuming they do.

---

# Real-Time Scheduling

Timing becomes increasingly important as the instrument grows.

The system may need to coordinate:

```text id="6v5yqg"
Motor 1 → step
Motor 2 → step
Motor 3 → step
Motor 1 → step
Motor 2 → step
...
```

The scheduler should investigate:

- Event timing
- Step timing
- Jitter
- Latency
- Scheduling accuracy
- Timing drift

Measurements may eventually include:

```text id="vvb5ey"
Target time:       100.000 ms
Actual time:       100.230 ms
Error:               0.230 ms
```

Actual results will be measured experimentally.

---

# Phase 7 — Audio Input

Once the physical instrument is reliable, the project can introduce audio.

The first goal is not AI.

The first goal is understanding the audio signal.

```text id="07rkjy"
Microphone / Audio
       ↓
Digital Audio
       ↓
Preprocessing
       ↓
Signal Analysis
```

Potential processing:

- Sampling
- Filtering
- Windowing
- Frequency analysis
- Spectrograms
- Peak detection
- Pitch estimation
- Timing detection

This phase creates the foundation for the later AI system.

---

# Phase 8 — Music Transcription

The system can eventually attempt to convert audio into musical events.

Example:

```text id="9v3nli"
Audio
 ↓
Detected frequency
 ↓
Estimated pitch
 ↓
Musical note
 ↓
Duration
 ↓
Timestamp
```

Example output:

```text id="0paz9e"
00:00.000 → C4
00:00.500 → E4
00:01.000 → G4
```

The accuracy of this process will be measured against known input.

---

# Phase 9 — AI-Assisted Audio Analysis

AI will be introduced only after a reliable baseline exists.

Potential AI applications include:

- Music transcription
- Note sequence interpretation
- Ambiguous pitch classification
- Timing interpretation
- Musical pattern recognition
- Comparison between signal-processing and AI approaches

The AI system should have measurable inputs and outputs.

For example:

```text id="2b9mwy"
Audio
 ↓
Signal Processing
 ↓
Candidate Notes
 ↓
AI Interpretation
 ↓
Musical Events
```

The project will compare:

```text id="r0pt6z"
Traditional Signal Processing
            VS
AI-Assisted Analysis
```

The goal is not to assume AI is better.

The goal is to determine where AI actually provides useful results.

---

# AI Evaluation

AI-generated musical interpretations will be evaluated using measurable criteria.

Potential measurements:

- Note accuracy
- Timing accuracy
- Transcription error rate
- Latency
- Confidence
- False detections
- Missed notes

Example:

```text id="uvn8ja"
Expected:
C4 - E4 - G4

Detected:
C4 - E4 - A4

Note Accuracy:
2 / 3
```

Actual measurements will be produced through experiments.

---

# Real-Time Instrument

The long-term system will combine:

```text id="l0b0qi"
Input
 ↓
Audio / Musical Interpretation
 ↓
Musical Event Representation
 ↓
Real-Time Scheduler
 ↓
Motor Control
 ↓
Physical Instrument
```

The final goal is to allow music to enter the system and eventually result in coordinated physical motor performance.

---

# Hardware / Software Boundary

One important architectural goal is separating the system into layers.

```text id="y2n7ds"
                 Music / Audio
                      ↓
              Musical Representation
                      ↓
                Event Scheduler
                      ↓
                Motor Commands
                      ↓
             Hardware Controller
                      ↓
                Motor Drivers
                      ↓
                   Motors
                      ↓
               Physical Sound
```

This allows the music-processing software to evolve without completely rewriting the motor-control system.

---

# Technology Stack

### Software

- Python
- Git
- GitHub
- Linux / development environment

### Hardware

- Stepper motors
- Motor drivers
- Microcontroller
- Appropriate power supply
- Mechanical components

### Audio

Potential tools/libraries for:

- Audio input
- Signal processing
- Frequency analysis
- Spectrograms
- Pitch detection

Specific libraries will be selected based on the hardware and experimental requirements.

### AI

Potential uses:

- Audio classification
- Music transcription
- Pattern interpretation
- Experimental comparison against signal-processing approaches

---

# Repository Structure

```text id="b1ympa"
ai-stepper-motor-music-instrument/
├── README.md
├── docs/
│   ├── hardware.md
│   ├── wiring.md
│   ├── sound-experiments.md
│   ├── timing.md
│   ├── audio-analysis.md
│   └── ai-audio.md
├── hardware/
│   ├── schematics/
│   ├── measurements/
│   └── configuration/
├── controller/
├── music/
├── audio/
├── ai/
├── ui/
├── tests/
├── experiments/
└── scripts/
```

---

# Branch Strategy

```text id="p0c86c"
main
develop

feature/hardware-baseline
feature/motor-control
feature/timing-engine
feature/note-mapping
feature/virtual-keyboard
feature/multi-motor
feature/audio-analysis
feature/ai-transcription
feature/real-time-input

experiment/motor-sound-*
experiment/timing-*
experiment/audio-*
experiment/ai-transcription-*
experiment/mechanical-*
```

### Branch Purpose

`main`
- Stable, demonstrated version

`develop`
- Integration branch

`feature/*`
- Focused implementation

`experiment/*`
- Hardware experiments
- Sound experiments
- Timing experiments
- AI comparisons
- Alternative mechanical designs

Hardware experiments should be documented even when they fail.

---

# Development Roadmap

## Phase 1 — Hardware Identification

- Identify motors
- Identify drivers
- Identify controller
- Identify power requirements
- Document wiring
- Establish safe operating conditions

## Phase 2 — Single Motor

- Basic motor control
- Direction
- Step count
- Speed
- Timing
- Repeatability

## Phase 3 — Sound Generation

- Identify sound mechanism
- Measure motor behavior
- Experiment with frequency
- Investigate resonance
- Determine usable range

## Phase 4 — Musical Notes

- Establish note representation
- Map motor behavior to notes
- Test repeatability
- Measure pitch consistency

## Phase 5 — Musical Scheduler

- Event representation
- Note timing
- Duration
- Sequences
- Playback

## Phase 6 — Input Interface

- Keyboard input
- Virtual keyboard
- Programmatic sequences
- MIDI-style events

## Phase 7 — Multiple Motors

- Multi-motor control
- Synchronization
- Scheduling
- Polyphony
- Timing measurements

## Phase 8 — Audio Analysis

- Audio input
- Sampling
- Filtering
- Frequency analysis
- Pitch detection
- Timing detection

## Phase 9 — AI Experiments

- AI transcription
- Candidate-note interpretation
- Timing interpretation
- AI vs signal processing
- Accuracy evaluation

## Phase 10 — Real-Time Instrument

- Real-time input
- Musical scheduling
- Multi-motor coordination
- Audio-to-motor pipeline
- Latency optimization
- Full demonstration

---

# Testing Strategy

## Hardware Tests

Test:

- Motor movement
- Direction
- Step accuracy
- Timing
- Temperature
- Power requirements
- Mechanical stability

## Software Tests

Test:

- Note representation
- Scheduling
- Event ordering
- Timing
- Input handling
- Motor commands

## Audio Tests

Test:

- Frequency detection
- Pitch detection
- Timing detection
- Noise handling

## AI Tests

Test:

- Note accuracy
- Timing accuracy
- False detections
- Missed notes
- Latency
- Confidence

---

# Experimental Documentation

Every major experiment should record:

```text id="znf3im"
Experiment
---------
Goal
Hardware
Software
Configuration
Input
Expected Result
Actual Result
Measurements
Problems
Changes
Conclusion
Next Experiment
```

For example:

```text id="zz8x4u"
Experiment:
Motor Sound Frequency

Goal:
Determine relationship between step frequency and audible pitch.

Variables:
- Step frequency
- Motor load
- Mechanical configuration

Measurements:
- Recorded audio
- Frequency spectrum
- Observed pitch

Conclusion:
Document measured relationship.

Next:
Test repeatability across multiple runs.
```

Failed experiments are useful data and should remain documented.

---

# Performance Measurements

Potential measurements include:

```text id="c9qglh"
Motor timing error
Audio latency
Pitch accuracy
Note detection accuracy
Synchronization error
CPU usage
Memory usage
AI inference latency
```

Example:

```text id="xy1y7y"
Target note:       A4
Expected frequency: 440 Hz
Detected frequency: X Hz
Error:              X Hz
```

Actual values will only be documented after measurement.

---

# Safety

Hardware experimentation must account for:

- Motor current
- Power supply limits
- Driver temperature
- Mechanical movement
- Moving components
- Wiring
- Emergency power cutoff

The software should not assume that a motor command is safe simply because the program accepts it.

Hardware limits should be documented before automated or long-duration experiments.

---

# Portfolio Evidence

Potential evidence includes:

- Hardware identification
- Wiring diagrams
- Motor-control software
- Sound experiments
- Musical note mapping
- Timing measurements
- Multi-motor synchronization
- Audio-processing pipeline
- AI transcription experiments
- AI vs traditional signal-processing comparison
- Latency measurements
- Physical demonstrations
- Engineering decisions
- Failed experiments and resulting improvements
