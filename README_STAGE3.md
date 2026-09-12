# Infinity Clock — Stage 3: Infinity Studio

Stage 3 extends Stage 2 with a real, data-driven clock editor while preserving the Stage 1/2 gallery and renderer.

## Included
- Dedicated Infinity Studio tab
- Live preview while editing
- Create new custom clock designs
- Edit custom designs
- Save / Save As / Delete
- Digital / Analog / Hybrid selection
- 10 palettes
- Layer/element list with add/remove/reorder
- Show seconds/date/hands/seconds-ring/background toggles
- Scale, rotation, opacity, glow, animation speed, text size controls
- Custom text
- Undo/redo session history (up to 30 snapshots)
- Custom clocks appear in Gallery under Custom
- Custom clock can be selected as the Home clock
- Renderer consumes the same ClockDesign model used by Gallery

## Stage 3 acceptance tests
1. App builds with zero Kotlin/Gradle compile errors.
2. Studio opens without crashing.
3. Creating a new clock changes the live preview immediately.
4. Digital/Analog/Hybrid switches render correctly.
5. Palette changes render immediately.
6. Every display toggle changes the preview correctly.
7. Scale/rotation/opacity/glow/animation/text-size sliders work.
8. Elements can be added, removed, and reordered.
9. Undo and redo restore previous design states.
10. Save persists the design for the current app session and it appears in Custom gallery.
11. Save As creates a distinct custom design.
12. Delete removes the custom design from the current session.
13. Selecting a custom design makes it the Home clock.
14. Core clock rendering remains functional without internet.
15. Final GitHub build must pass before Stage 4 starts.

Note: persistent on-device custom-design serialization is intentionally scheduled for the next persistence-focused hardening pass; Stage 3 keeps session state in memory so the editor can be developed and tested without introducing unnecessary storage complexity at this stage.
