# Infinity Clock — Stage 10

## Bedside / Full-Screen Mode

Stage 10 adds a real Android bedside clock mode on top of Stage 9.

### Implemented
- Dedicated full-screen bedside mode from the Home screen.
- Uses the currently selected clock design, including persistent custom/AI clocks.
- Keeps the display awake while bedside mode is active.
- Hides system bars while active using the supported WindowInsets API.
- Back button and an on-screen exit control both leave bedside mode.
- Tap anywhere toggles the bedside controls so the clock can run cleanly at night.
- Existing Gallery, Studio, AI, Widgets, Live Wallpaper, Time Lab, persistence and performance modes are preserved.
- No network is required.

### Safety / platform behavior
- The feature does **not** claim to replace the Android system lock-screen clock.
- It only controls the app window while Infinity Clock is visibly running.
- System bars are restored when the mode exits or the composable is disposed.

### Validation performed in this environment
- ZIP integrity: PASS
- Kotlin source structural balance checks: PASS
- No binary APK/device test was possible here because a complete Android SDK/Gradle toolchain is not available in the execution environment.

### Acceptance test
1. Build with the repository GitHub Actions workflow.
2. Install the debug APK on the target Android phone.
3. Open Infinity Clock → Home.
4. Tap **Bedside full-screen mode**.
5. Verify the selected clock fills the screen and the screen stays awake.
6. Tap the screen to hide/show controls.
7. Press Back or the exit button.
8. Verify normal navigation returns and system bars are restored.
9. Repeat using a custom/AI-generated clock.
10. Verify the app still retains Stage 5–9 functions.

Do not advance to the next stage until these checks pass.
