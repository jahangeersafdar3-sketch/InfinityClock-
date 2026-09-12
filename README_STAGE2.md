# Infinity Clock — Stage 2

Stage 2 extends the Stage 1 foundation into a real clock gallery and a reusable visual rendering engine.

## What is implemented
- 120 clock designs generated as structured `ClockDesign` presets.
- 40 Digital + 40 Analog + 40 Hybrid designs.
- Search and category filters.
- Favorites.
- Live previews for every gallery card.
- Reusable digital, analog and hybrid renderers.
- Multiple visual palettes, hand styles, ring variants, typography variants and date/seconds combinations.
- Selected clock is shown on Home.
- Smooth time-driven updates without network access.
- Core app remains offline.

## Important implementation note
The 120 designs are data-driven variations rendered by the same trusted clock engine. They are not 120 image files. This keeps the APK smaller and makes future editor/AI/widget integration possible without rewriting every clock.

## Build/test
This runtime cannot execute a full Android Gradle build because the container does not have Gradle/Android SDK installed. The GitHub workflow was updated to provision Gradle 8.10.2 and build `assembleDebug`.

### Stage 2 acceptance tests
1. GitHub Actions `assembleDebug` succeeds.
2. APK installs on the target Android phone.
3. Home clock updates from system time.
4. Gallery opens and scrolls through 120 designs.
5. Digital/Analog/Hybrid filters return the expected 40/40/40 counts.
6. Search narrows results without crashes.
7. Favorite/unfavorite works and Favorites filter shows saved items.
8. Selecting a gallery clock returns to Home and renders that clock.
9. Offline mode: gallery and clocks continue to work with network disabled.
10. Fast scrolling does not crash or show corrupted previews.
11. Background/foreground and app restart recover correctly.
12. No uncontrolled network or background service is introduced by Stage 2.

**Do not start Stage 3 until these checks pass.**
