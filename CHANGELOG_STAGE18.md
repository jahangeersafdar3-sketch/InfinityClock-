# Infinity Clock — Stage 18 / Release 1.0.0

Stage 18 is the final release-hardening stage in the staged build plan.

## Release hardening
- Production version metadata: `1.0.0` / version code `18`.
- JVM unit-test dependency enabled for release contract tests.
- Added pure release diagnostics for version sanity and user-text sanitization.
- CI now runs unit tests before producing the debug APK.
- CI also runs Android lint where supported by the toolchain.
- Release signing is intentionally NOT hard-coded; use GitHub Actions/Gradle secrets for a real signing key.
- No private API keys, credentials, or signing materials are stored in source control.

## Functional scope retained
Stages 1–17 remain included: clock gallery, Studio, AI pipeline, widgets, live wallpaper, Time Lab, persistence, performance modes, bedside mode, and premium UI.

## Known platform limitations
Android launchers, exact alarms, notification permission, live wallpaper previews, and OEM power-management policies can vary by device/version. The app uses supported Android APIs and graceful fallbacks rather than claiming universal behavior.
