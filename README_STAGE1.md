# Infinity Clock — Stage 1

Stage 1 is the foundation only.

## Included
- Kotlin + Jetpack Compose
- Material 3
- Offline core clock
- Live digital clock engine
- Date/day display
- 12/24-hour-ready architecture
- Seconds toggle
- Home / Clocks / Settings navigation
- Dark/AMOLED-ready theme foundation
- DataStore dependency prepared for persistent settings
- GitHub Actions debug APK build

## Build
Use JDK 17 and Android SDK 35.

```bash
./gradlew assembleDebug
```

APK:
`app/build/outputs/apk/debug/app-debug.apk`

## Stage 1 acceptance tests
1. Clean build succeeds.
2. APK installs.
3. App launches without crash.
4. Clock tracks device time.
5. Seconds toggle works.
6. Navigation works.
7. Core clock works without internet.
8. App survives close/reopen.
9. No blocking background service is used.
10. GitHub Actions produces the debug APK.

Stage 2 must not be started until these checks pass.
