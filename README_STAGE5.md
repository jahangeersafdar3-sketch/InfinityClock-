# Infinity Clock — Stage 5

Stage 5 adds **real Android Home Screen widgets** using the official AppWidget/RemoteViews system. These are launcher widgets, not an in-app simulation.

## Included
- Small, Medium, and Large widget entries in the Android widget picker.
- Each widget is resizable and independently configurable.
- Per-widget selection from 120 clock design IDs (40 Digital, 40 Analog, 40 Hybrid).
- Per-widget toggles for seconds, date, and 12/24-hour display.
- Live `TextClock` time rendering in the launcher so the clock keeps updating without the app being open.
- Widget background/accent styling based on the selected clock family.
- Tap a widget to open Infinity Clock.
- Widget updates for time/timezone changes plus normal AppWidget scheduling.
- No cloud or account requirement.

## Important implementation note
Android launcher widgets use `RemoteViews`, which intentionally supports a smaller set of UI primitives than the full Compose renderer. Stage 5 therefore provides a reliable widget renderer rather than pretending the entire Compose canvas can be copied into a launcher widget. The full visual clock engine remains inside the app.

## Acceptance test
1. Build the APK with GitHub Actions.
2. Install it on the phone.
3. Long-press the Home Screen -> Widgets -> Infinity Clock.
4. Confirm Small / Medium / Large appear.
5. Add each and confirm the configuration screen opens.
6. Choose different designs/options and add multiple widget instances.
7. Lock the phone for a few minutes and verify time continues to update on the Home Screen without opening the app.
8. Tap a widget and confirm Infinity Clock opens.

Per the project workflow, **Stage 6 should not start until Stage 5 builds and this device acceptance test passes**.
