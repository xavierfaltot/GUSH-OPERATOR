# GUSH OPERATOR — Architecture

## System overview

GUSH OPERATOR is organized as a closed feedback loop:

`VIDEO → VIEWER → EEG / PHYSIOLOGY → SIGNAL PROCESSING → VIEWER STATE → DESIRE MODEL → EDITING ENGINE → VIDEO GENERATION → VIDEO`

## 1. Signal acquisition

Target input is a non-invasive EEG stream, with OpenBCI as the first hardware integration target. Additional channels may later include eye movement, pupil dilation, heart rate, breathing and body motion.

The acquisition layer must expose timestamped samples and signal-quality metadata. Every sample must be synchronized to the video timeline.

## 2. Signal processing

Raw EEG is filtered, normalized against a session baseline and transformed into a small control vocabulary rather than treated as literal thought decoding.

Initial derived values:

- `attention`
- `activation`
- `stability`
- `shift`
- `response`

The processor works on rolling time windows and emits smoothed values between 0 and 1.

## 3. Calibration

Each session starts with a short calibration sequence. Contrasting visual stimuli establish a personal baseline for the current session.

Calibration output:

- signal floor / ceiling
- noise profile
- per-channel weighting
- response latency estimate
- initial attention / activation ranges

## 4. Image analysis

Every displayed segment carries machine-readable metadata describing its visual and narrative properties.

Initial descriptors:

- subject
- shot scale
- motion
- density
- light
- rhythm
- space
- continuity
- semantic tags

This makes it possible to connect a physiological change to the visual event that preceded it.

## 5. Desire Model

The Desire Model combines live signals, session history and operator parameters.

Primary weights:

- `desire`
- `attention`
- `memory`
- `novelty`
- `continuity`
- `resistance`

The model produces a state vector used by the editing engine.

## 6. Editing engine

The V0 engine scores five abstract directions:

- `CONTINUE`
- `INTENSIFY`
- `RETURN`
- `MUTATE`
- `BREAK`

The selected direction is the highest-scoring result after operator weighting, live-state weighting and controlled randomness.

Later versions will expand these directions into concrete scene operations such as camera distance, character persistence, location change, rhythm, abstraction and narrative branching.

## 7. Generation layer

The generation layer receives:

1. current visual state
2. session memory
3. selected editing direction
4. operator style parameters

It outputs the next playable segment while the current segment is still being viewed.

The architecture should keep the generation provider abstract so multiple backends can be tested.

## 8. Buffer and latency

GUSH works with a short future buffer. Every reaction has a physiological latency, and every generated shot has a compute latency.

The scheduler therefore tracks:

- event timestamp
- estimated reaction latency
- generation start
- generation completion
- playback deadline

The target is continuous playback with the editing system always preparing the immediate future.

## 9. Session memory

Every cycle is logged as a `GUSH EVENT`:

```json
{
  "time": 12.4,
  "shot_id": "shot-008",
  "signals": {
    "attention": 0.81,
    "activation": 0.63
  },
  "model": {
    "desire": 0.74,
    "novelty": 0.31
  },
  "decision": "INTENSIFY"
}
```

The complete event history becomes the GUSH MAP and can later be exported alongside the generated film.
