# Infinity Clock — Stage 6

Stage 6 adds a **real Android Live Wallpaper** and hardens the Stage 5 widget resources so the project has a complete, consistent widget manifest/resource set.

## Stage 6 included

### Real Live Wallpaper
- Registers `InfinityLiveWallpaperService` as a genuine Android `WallpaperService`.
- Appears in the device's supported live-wallpaper chooser.
- Uses the currently selected Infinity Clock ID from app state.
- Renders Digital, Analog and Hybrid families directly with Android `Canvas`.
- Updates once per second for a smooth clock without requiring the main app to stay open.
- Stops the frame loop when the wallpaper is not visible to reduce unnecessary battery work.
- Draws at the actual wallpaper surface size, so it scales to different phone resolutions.
- Handles seconds, hands, ticks, date and accent/background styling in the wallpaper renderer.

### App integration
- Settings now has a **Set Live Wallpaper** action.
- The action requests Android's official live-wallpaper component chooser/preview.
- The selected clock ID is persisted in app state when a gallery selection is made, so the wallpaper can reuse it.
- App startup now restores the last selected clock ID instead of always resetting to the first clock.

### Stage 5 hardening
- Added the missing Small / Medium / Large widget layouts and provider XML resources referenced by the Stage 5 manifest.
- Added required widget strings.
- Each widget provider now points to its own layout/provider metadata and the configuration activity.

## Platform truth
This stage provides a real **Home Screen Live Wallpaper** through Android's supported `WallpaperService` API. It does **not** claim to replace the system Lock Screen clock on every Android device, because lock-screen clock customization is device/OEM/API dependent.

## Battery/performance design
- Wallpaper animation uses one lightweight scheduled render loop.
- Loop runs only while the wallpaper engine reports itself visible.
- No network, cloud, account or API key is required.
- No arbitrary generated code is executed by the wallpaper.

## Acceptance test
1. Build the project with GitHub Actions and confirm `assembleDebug` succeeds.
2. Install the APK on the Android phone.
3. Open Infinity Clock -> Clocks and select a digital, analog and hybrid design one at a time.
4. Open Settings -> Live Wallpaper -> **Set Live Wallpaper**.
5. Confirm Android opens Infinity Clock in its live-wallpaper preview/chooser.
6. Apply the wallpaper and return to the Home Screen.
7. Confirm the selected clock is visibly rendered and the seconds/hands advance every second.
8. Change the selected clock inside the app and reapply the wallpaper; confirm the new family is rendered.
9. Leave the wallpaper preview/home screen and verify the render loop stops when it is no longer visible.
10. Confirm Stage 5 Small / Medium / Large widgets still appear in the launcher widget picker and can be configured.

## Workflow rule
Per the project workflow: **Build -> Test -> Performance check -> Error check -> Fix -> Rebuild -> Retest -> PASS -> Next Stage**.

Because this environment does not contain the Android SDK/Gradle executable, I could not honestly claim a device/APK build here. The source/resource checks were completed, but the final PASS still needs to come from GitHub Actions + your phone.
