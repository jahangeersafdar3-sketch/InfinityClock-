# Infinity Clock — Stage 18

## Final QA & Release Hardening

Stage 18 is the final stage of the current roadmap. It does not add a new feature family; it hardens the full Stage 1–17 product for release.

### Included
- Production release metadata (`1.0.0`, version code `18`).
- JVM release-contract tests.
- CI sequence: unit tests → Android lint → debug APK build → APK artifact upload.
- Explicit secure-signing guidance; no private signing material is committed.
- Security notes for AI providers and credentials.
- Final device QA checklist covering core flows, widgets, wallpaper, alarms, offline mode, performance and bedside mode.

### Required final verification
This stage is **source/CI-ready**, but a truthful final PASS still requires GitHub Actions plus physical-device testing. The local environment used to assemble this package does not contain the Android SDK/Gradle toolchain, so no claim is made that an APK was compiled or tested here.

### Final build rule
`Build → Test → Performance → Error Check → Fix → Rebuild → Retest → PASS`

Only after that cycle passes should the generated APK/AAB be distributed.
