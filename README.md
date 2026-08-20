# Lull

A sleep-native learning app for high-stakes college students.

**Learn around sleep, not while asleep.**

## The thesis

You cannot teach a sleeping brain new complex material. What is real:

1. Protecting sleep improves learning capacity.
2. A focused review right before bed feeds the overnight consolidation window (and can steady sleep).
3. Audio cues during sleep can reinforce already-studied material (TMR) — but not teach it.
4. Morning retrieval practice (the testing effect) is what builds durable memory.

Every feature and every word respects this. No "learn while you sleep" claims. The app never costs the user sleep.

## The daily loop

| Phase | Duration | What happens |
|---|---|---|
| **Evening encode** | ~10 min | Wren teaches one slice, ends with active recall. Timed for the pre-sleep window. |
| **Overnight** | — | Optional, honest audio reinforcement of tonight's material. Protect + measure sleep. Labeled "reinforcement, not new learning." |
| **Morning retrieve** | ~5 min | Interactive quiz. Right answers get a why; wrong answers get a correction *and* a why. Misses re-queue on a spaced schedule. This is the hero moment. |
| **Wren** | always | Sidebar tutor, source-grounded on the user's own materials. |

Curriculum is a sleep-anchored spaced-repetition schedule: items resurface based on morning performance **and** sleep signal.

## Audience

Memorization-heavy, high-stakes tracks first — pre-med/bio, nursing, law, MCAT/USMLE/bar.

JTBD: *"help me actually retain this in 6 weeks without wrecking myself."* Then widen.

## Running the prototype

Open `lull-prototype.html` in any browser. No build, no server, no dependencies.

Append `#selftest` to the URL to run the built-in assertions (scheduler, content integrity, and a guardrail check that no copy anywhere claims sleep-learning). Results print to the console.

## Design system

**Signature = two faces.** Same app, two circadian states: deep candlelit night ↔ bright morning. Auto-selected by time of day; a preview toggle lives in settings.

Fonts: **Fraunces** (display — headlines and Wren's voice, used sparingly), **Hanken Grotesk** (UI/body).

| Token | Night | Morning |
|---|---|---|
| sky | `#14111f` → `#1c1830` | `#fbf6ee` → `#fceede` |
| surface | `#221d35` | `#ffffff` |
| accent | `#e7a94e` / `#f0c578` | `#e39a34` (text `#b5771e`) |
| ink | `#ece4d6` | `#2a2333` |
| mute | `#9c94ac` | `#7a7286` |

Feedback uses a good green and a soft coral — never alarm red. All theming flows through `data-theme` + CSS custom properties.

## UX principles (non-negotiable)

- One primary action per screen. Single hero button in the bottom thumb zone. Settings in the top corner, out of the easy path.
- The quiz is full-screen and single-focus with **no live score** — score anxiety kills recall. Reasoning appears as a calm reveal after answering.
- Gamify consistency and sleep, never raw hours. A rested, consistent student wins.
- Copy in Wren's voice: plain verbs, sentence case, active, never selling. Errors give direction, not apology.

## Wren

Warm, gender-neutral human name (dawn songbird → morning). Calm mentor at night, crisp coach in the morning — one identity, two energies.

Voice: warm, lower-pitched, gender-ambiguous by default, user-selectable across masc/fem/neutral. Softer and slower at night, brighter in the morning. A/B test on trust and 30-day retention.

## What's stubbed vs. real

**Stubbed:** the sample content object (one lesson + four questions), Wren's canned replies, the sleep signal. No auth, no storage, no network.

**Real:** navigation, two-face theming, the encode flow, quiz logic, the spaced-return scheduler and its copy, and the sidebar. All of it is built to extend.

## Roadmap

1. **Tutor** — LLM API for teach/quiz/sidebar, source-grounded on uploaded materials (RAG). Socratic "guide, don't dump" by default.
2. **Curriculum engine** — any book or subject → a spaced schedule over N days; generates the evening slice and the morning questions.
3. **Spaced repetition** — scheduler keyed to morning performance and sleep. Misses resurface.
4. **Personalization** — import NotebookLM / LLM history / connected apps to calibrate level and tone.
5. **Sleep integration** — HealthKit and wearables for sleep signal. Honest overnight audio reinforcement (TMR-style cueing of that night's material only). Protect-sleep guardrails.
6. **Accounts + storage**, then privacy as a marketed feature. Data-hungry, student, health-adjacent — trust is the moat.

## Guardrails

- No "learn while asleep" claims, anywhere.
- Never reduce the user's sleep.
- Source-ground the tutor. If it isn't in the user's materials, Wren says so rather than inventing.
- Privacy-first.
- Non-punitive tone throughout.
