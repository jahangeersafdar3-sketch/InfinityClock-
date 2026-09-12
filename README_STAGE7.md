# Infinity Clock — Stage 7

Stage 7 adds the app's **Time Lab**: real daily alarms, countdown timer, stopwatch, and live world clocks. The tools are reachable from the Home screen and Settings without adding a sixth item to the bottom navigation.

## Included

### Daily alarms
- Multiple independent alarms.
- Persistent alarm list using local Android storage.
- Enable/disable and delete controls.
- Android `AlarmManager` scheduling with an exact-alarm attempt and safe inexact fallback when the OS does not grant exact-alarm access.
- High-importance notification channel.
- Android 13+ notification permission request from the Time Lab.
- Alarm automatically schedules its next daily occurrence after firing.
- Re-schedules enabled alarms after device boot, app replacement, time changes, and timezone changes.
- Fully offline; no account or server required.

### Countdown timer
- 1, 5, 10, and 15 minute presets.
- Start/pause/reset.
- Live one-second countdown.

### Stopwatch
- Start/pause/reset.
- Live elapsed time.

### World Clock
- Live clocks for New York, London, Dubai, Karachi, Delhi, Singapore, Tokyo, and Sydney.
- Uses Android/Java timezone rules rather than hard-coded offsets, so DST changes are handled by the platform timezone database.

## Platform truth
- Notifications require user permission on Android 13 and newer.
- Exact alarm access can be restricted by Android. Stage 7 attempts `setExactAndAllowWhileIdle()` and falls back to `setAndAllowWhileIdle()` rather than crashing or pretending exact delivery is guaranteed.
- Alarms are designed as daily local-time alarms.
- The Time Lab UI is an in-app utility; it does not claim to replace OEM/system alarm apps.

## Acceptance test
1. Build with GitHub Actions and confirm the debug APK is produced.
2. Install on the phone and open Home -> **Time Lab**.
3. Add an alarm 2–3 minutes ahead, enable notifications when Android asks, lock the phone, and verify the alarm notification appears.
4. Toggle the alarm off and back on; confirm scheduling follows the switch state.
5. Delete an alarm and confirm its notification does not fire.
6. Start a 1 minute timer, pause it, resume it, and reset it.
7. Run the stopwatch for at least 10 seconds; pause and reset.
8. Open World Clock and verify city times update each second.
9. Reboot the phone with an enabled daily alarm and confirm it remains scheduled.
10. Change the device time/timezone and confirm enabled alarms are rescheduled.

## Workflow rule
**Build -> Test -> Performance check -> Error check -> Fix -> Rebuild -> Retest -> PASS -> Next Stage**

This environment does not include the Android SDK/Gradle executable, so an actual APK/device PASS cannot be honestly claimed here. Source-level checks were performed; final PASS must come from GitHub Actions and the phone acceptance test above.
