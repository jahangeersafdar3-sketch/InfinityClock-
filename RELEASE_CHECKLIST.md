# Infinity Clock 1.0.0 — Final QA Checklist

## Automated / CI
- [ ] `gradle test` passes.
- [ ] `gradle lint` passes with no new blocking errors.
- [ ] `gradle assembleDebug` passes.
- [ ] APK artifact is produced by GitHub Actions.
- [ ] Release build is signed only through a secure keystore/CI secret.

## Core app
- [ ] App launches and survives rotation/process recreation.
- [ ] Gallery search, filters and favorites work.
- [ ] Studio save/edit/delete/undo/redo works.
- [ ] AI generation/refinement stays inside the structured ClockDesign pipeline.
- [ ] Custom clocks survive app restart.

## Device integration
- [ ] Small/medium/large widgets can be added and configured.
- [ ] Multiple widget instances retain independent settings.
- [ ] Live wallpaper can be previewed/applied and stops work while hidden.
- [ ] Alarms notify correctly after permission is granted.
- [ ] Timer and stopwatch continue correctly when app UI is changed.
- [ ] Bedside mode keeps the display awake and exits cleanly.

## Performance / reliability
- [ ] Balanced mode is stable on a mid-range device.
- [ ] Battery-saver mode reduces update frequency.
- [ ] No obvious ANR, runaway animation, or memory growth during a 15-minute soak.
- [ ] Offline core features still work with network disabled.
- [ ] Dark/AMOLED themes remain readable.

## Final device note
The repository is considered release-ready only after the GitHub Actions build succeeds and the above device checks pass on the target phone and at least one additional modern Android device.
