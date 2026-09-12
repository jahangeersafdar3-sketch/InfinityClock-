# Infinity Clock — Stage 4

## Infinity AI Clock Agent

Stage 4 adds a safe AI-style design pipeline on top of the Stage 3 clock engine and Studio.

### Included
- Dedicated Infinity AI tab
- Natural-language clock prompt input
- Offline structured design interpreter (no API key required)
- Digital / Analog / Hybrid intent parsing
- Style/color/mood keyword parsing
- Seconds/date/show/hide parsing
- Glow, text-size and animation-speed interpretation
- Safe ClockDesign validation with bounded numeric ranges
- Live rendering using the real clock renderer
- AI quality critique with readability/performance notes
- Save & edit flow into Infinity Studio
- Remix flow
- Provider abstraction (`ClockAiProvider`) so a real online model can be added later without changing the renderer
- Generated output is data only; no generated Kotlin/JavaScript/code is executed
- Core stage remains usable offline

## Stage 4 test checklist
1. Clean build succeeds.
2. AI tab opens.
3. Prompt examples populate.
4. Generate produces a validated ClockDesign.
5. Preview uses live device time, not a static image.
6. Save & edit opens the design in Studio.
7. Remix changes the design and remains within validated ranges.
8. Invalid/empty prompts do not crash the app.
9. Core AI flow works with internet disabled.
10. No private provider API key is embedded in the APK.

## Important
The offline interpreter is intentionally deterministic. It provides a working Stage-4 agent foundation without pretending to be a remote LLM. A production online provider can later implement the same `ClockAiProvider` interface.

Stage 5 should not begin until this stage builds and passes device testing.
