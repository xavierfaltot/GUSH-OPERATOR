# GUSH OPERATOR

**Brain-driven generative cinema.**

GUSH OPERATOR is an experimental system that turns neural and physiological reactions into real-time editing decisions. A viewer watches a film, sensing hardware captures changes in their state, the system builds a live Desire Model, and an editing engine decides what should happen next.

The project starts with a practical V0: a browser-based simulator that generates synthetic EEG-like signals and uses them to drive an autonomous editing state machine. This lets us validate the logic before connecting real sensing hardware and a generative video API.

## Core loop

`IMAGE → VIEWER → SIGNAL → DESIRE MODEL → EDITING DECISION → NEXT IMAGE → VIEWER`

## Parameters

- **DESIRE** — weight given to motifs associated with stronger reactions
- **ATTENTION** — persistence of engagement
- **MEMORY** — influence of previous reactions and motifs
- **NOVELTY** — appetite for new visual information
- **CONTINUITY** — preservation of world, characters and narrative
- **RESISTANCE** — distance introduced between predicted preference and the next edit

## Project stages

**V0 — Brain Cut**  
Synthetic signal + autonomous edit decisions + local clip pool.

**V1 — Brain Input**  
Connect real EEG hardware (OpenBCI first target), calibration and signal-quality monitoring.

**V2 — Brain Generate**  
Turn edit decisions into prompts / control instructions for a generative video backend.

**V3 — Desire Loop**  
Long-session memory, individual adaptation, branching narrative and exportable GUSH MAP.

## Run the V0 prototype

Open `prototype/index.html` directly in a browser.

The prototype simulates five live signals, computes a Desire Model, scores five possible edit directions and selects the strongest one every few seconds.

## Repository

- `prototype/index.html` — runnable browser prototype
- `config/gush-default.json` — default operator parameters
- `docs/architecture.md` — technical architecture
- `docs/roadmap.md` — development roadmap

---

**GUSH OPERATOR**  
`BRAIN → DESIRE → IMAGE → BRAIN`
