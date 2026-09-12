# Infinity Clock — Stage 8

Stage 8 is the **Persistence + Performance Foundation** stage.

## Included
- Custom Studio and AI-generated clocks persist locally across app restarts.
- Favorites persist locally.
- Dark/AMOLED preference persists locally.
- Selected clock is restored and is saved whenever a clock is selected/saved.
- Custom clock IDs are collision-resistant within normal app usage.
- Persisted designs are validated and safely recovered; corrupted entries are ignored instead of crashing the app.
- Widget lookup can resolve persisted custom designs as well as built-in designs.
- A single app-level Compose clock ticker feeds all visible clock renderers through `LocalClockNow`, replacing many independent timing loops in gallery/editor/preview clocks.
- The centralized ticker runs at 250 ms to keep seconds visually smooth while reducing redundant coroutine loops.
- Existing alarms, timer, stopwatch, world clocks, widgets, live wallpaper, Studio and Infinity AI are preserved.

## Platform truth
- Local persistence uses Android SharedPreferences + JSON for deterministic offline storage.
- Widgets remain subject to Android RemoteViews limitations; the launcher widget renderer is not an arbitrary Compose canvas.
- This stage does not claim an exact universal refresh rate for every Android launcher.

## Acceptance test
1. Build with GitHub Actions; APK must compile successfully.
2. Create a custom Studio clock, close the app, reopen it, and verify it remains in the Custom gallery.
3. Generate an AI clock, close/reopen, and verify it remains available.
4. Favorite a built-in and a custom clock; restart the app and verify both favorites remain.
5. Select a custom clock, restart, and verify Home restores that clock.
6. Change dark/AMOLED setting, restart, and verify it persists.
7. Add a widget configured to a custom persisted clock and confirm it still displays after app restart.
8. Open Gallery with many clock cards and verify scrolling remains responsive; confirm no visible clock freezes.
9. Run Time Lab alarms/timer/stopwatch/world clocks and confirm Stage 7 behavior remains intact.
10. Check logcat for crashes while switching Home, Clocks, Studio, AI and Settings.

## Workflow rule
**Build -> Test -> Performance check -> Error check -> Fix -> Rebuild -> Retest -> PASS -> Next Stage**

This environment does not contain the Android SDK/Gradle executable, so a real APK/device PASS cannot be claimed here. Source-level contract checks are included; the final PASS must come from GitHub Actions plus the phone acceptance test above.
