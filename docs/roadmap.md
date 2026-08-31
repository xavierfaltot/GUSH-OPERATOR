# GUSH OPERATOR — Roadmap

## V0 — Brain Cut

Goal: prove the decision loop before hardware integration.

- synthetic EEG-like signal generator
- live signal monitor
- adjustable Desire Model parameters
- five editing directions
- automatic decision cycle
- event log / GUSH MAP preview
- browser prototype

Success criterion: the operator can change the behaviour of the autonomous editor and clearly observe the resulting decision pattern.

## V0.2 — Clip engine

Goal: replace abstract decisions with visible edits.

- local media folder / clip manifest
- clip metadata
- decision-to-clip scoring
- seamless next-clip queue
- fullscreen playback
- session recording manifest

## V1 — Brain Input

Goal: replace simulated signals with live sensing.

- OpenBCI adapter
- device connection status
- channel quality monitoring
- baseline calibration
- timestamp synchronization
- rolling-window feature extraction
- simulator / hardware switch

## V1.5 — Multimodal sensing

- heart-rate input
- eye / pupil input
- motion input
- confidence weighting across modalities

## V2 — Brain Generate

Goal: generate the next scene from the current state.

- provider abstraction
- generative video API adapter
- prompt/control compiler
- current-frame continuity
- future buffer
- retry / fallback strategy
- latency dashboard

## V3 — Desire Loop

Goal: make the film increasingly specific to the viewer over time.

- long-session memory
- motif tracking
- character persistence
- narrative state
- adaptive parameter weighting
- GUSH MAP export
- final film assembly

## Experimental questions

1. How long does calibration need to be before useful decisions emerge?
2. Which EEG-derived features are stable enough for artistic control?
3. What decision interval feels cinematic rather than reactive?
4. How much resistance creates surprise without destroying continuity?
5. How much future buffer is required for uninterrupted generated playback?
6. Can two sessions starting from the same seed diverge visibly within ten minutes?
